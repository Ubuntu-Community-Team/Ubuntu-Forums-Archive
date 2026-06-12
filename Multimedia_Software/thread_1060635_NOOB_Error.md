---
title: "NOOB Error"
date: 2009-02-04
forum: Multimedia Software
---

### Post by rodbuilder63 on 2009-02-04
Hi All

I did something really silly late last night and hope maybe some of you can help me out.  I changed the video resolution on my monitor with the screen resolution tool and now when I logon all I get is a black screen with the error message that my monitor doesn't support this resolution.  What can I do?

I am running Ubuntu Ibex v8.10
I am using Gnome desktop but I have the option of the KDE desktop

Mark Nowakowsky

---

### Post by SuperSonic4 on 2009-02-04
Drop into recovery mode and click on try to fix x-server.

```
sudo dpkg-reconfigure xserver-xorg
``` may also work if you can get a cli

---

### Post by rodbuilder63 on 2009-02-06
Hey SuperSonic4

I tried that and didn't help, what I need to find out is how to change the "script" for my user that affects video during the gnome login process.  What is the name of the conf file and how do I change it?

---

### Post by cariboo on 2009-02-06
If you have another computer can you use the remote desktop viewer to log in and change the resolution?

to start vino start in recovery mode and drop to a root prompt, type:

```
dhclient eth0
```

to start networking, next type:

```
vino-server &
```

Then when you are back at the prompt type:

```
exit
```

Then select resume and continue booting.

Jim

---

