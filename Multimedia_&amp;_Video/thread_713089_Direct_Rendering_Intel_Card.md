---
title: "Direct Rendering? Intel Card"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by benpage26 on 2008-03-02
Hi,

In my laptop i have a "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller".  I don't think I have set it up properly, and therefore, i don't think i am using it to its full capacity.

For example
```

ben@winegums:~$ glxinfo |grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```

I always thought my graphics card should be direct rendering, but i have no idea when it comes to graphics cards. all i know is mine isn't the most powerful out there.  But i used to be able to run "black and white 2" on windows so it can't be that bad.

Is there any way to make sure my graphics card is set to its full potential.

Thanks .

---

### Post by furyy on 2008-03-02
Somehow LIBGL_ALWAYS_INDIRECT got set. 
Run in terminal ```
export LIBGL_ALWAYS_INDIRECT=no 
```
but it has effect only if apps are launched from that terminal then.

Check if it is in .bashrc ```
 nano ~/.bashrc   
```

---

### Post by benpage26 on 2008-03-02
[edit]

I just tried it, and glxinfo still says no..?

```
ben@winegums:~$ export LIBGL_ALWAYS_INDIRECT=no
ben@winegums:~$ glxinfo |grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```
Thank you.


Could you explain to me the purpose of LIBGL_ALWAYS_INDIRECT.  Is there any reason you would want it set to yes?


And what is .bashrc?  Is that a script that is run at logon

Thanks again.

---

