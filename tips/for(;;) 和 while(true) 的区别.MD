# for(;;) 和 while(true) 的区别
---
看了很多源码，写死循环的地方都是用**for(;;)**而不是**while(true)**，今天才了解到原来区别是编译成汇编代码不一样。

*  while(true)编译后的汇编代码
```
mov eax,1
test eax,eax
je foo+23h
jmp foo+18h
```
*  for(;;)编译后的汇编代码
```
jmp foo+23h
```

对比之下不难发现，虽然最终效果一致，但是**for(;;)**的代码简洁很多，并且不占用寄存器。