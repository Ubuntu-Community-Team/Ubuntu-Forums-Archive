---
title: "Gimp 2.8 wont start in Ubuntu, always did &amp; now it doesn't. Help please"
date: 2015-08-18
forum: Multimedia Software
---

### Post by peter_b2 on 2015-08-18
I am running ubuntu 14.04 and gimp 2.8 successfully for about 2 months. Yesterday it stopped opening, I see the icon, the white triangle , I see the opening dialogue as it loads up with  all its requirements but after that nothing. I have reloaded the program and the result is the same. Anybody run into this?

thanks in advance

Peter b

---

### Post by steeldriver on 2015-08-18
Hello and welcome to the forums

Have you tried starting gimp from a terminal, and noting any errors? 

Sometimes it's something corrupted in your ~/.gimp-2.8 directory - you can always rename (mv) it and try again

---

### Post by peter_b2 on 2015-08-19
Hello steeldriver

thank you for your reply. I see no errors when I type gimp in the terminal. What do you mean by renaming it? Obviously I am a beginner at this.

thanks

---

### Post by SeijiSensei on 2015-08-19
```

cd ~
mv .gimp-2.8 .gimp-2.8.old
gimp

```

Any better?

---

### Post by peter_b2 on 2015-08-19
hello  SeijiSensei: 



typed your code and the following was the result : - bash: cd: -m: invalid option
cd: usage: cd [-L|[-P [-e]] [-@]] [dir]

This occurs to me, do I need to type it exactly as I see it?

 getting somewhere ! thanks for your help

---

### Post by peter_b2 on 2015-08-20
SeijiSensei

Yes! input the code exactly as I see it and everything runs properly.

thanks again,
Peter b2

---

