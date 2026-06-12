---
title: "Bumblebee (optirun) problem"
date: 2012-04-18
forum: Multimedia Software
---

### Post by arcelivez on 2012-04-18
Hello,

I keep getting the error when I try to use optirun:
arturas@Arturas-Aspire-5750G:~$ optirun google-chrome 
[ERROR]You've no permission to communicate with the Bumblebee daemon. Try adding yourself to the 'bumblebee' group
[ERROR]Could not connect to bumblebee daemon - is it running?

Background: I bought a new laptop two days ago, which has the gpu with nvidia optimus, I have Ubuntu 12.04 beta2, I did the following:

I installed bumblebee following the instruction on [https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

I added myself to the bumblebee group with no errors:
```
sudo usermod -a -G bumblebee $USER
```

And I started bumblebee daemon also with no errors:
```
bumblebeed --daemon

```

But I seem to be getting errors when trying to run anything with optirun?
Can anyone help?

---

### Post by arcelivez on 2012-04-18
Hmm, it kind of got solved by restarting again. Quite strange, since before trying to run it the first time I'm pretty sure I had restarted. But I'm glad it works now.

---

### Post by Lekensteyn on 2012-04-30
You need to re-login (or reboot). See [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969)

---

### Post by plazaster on 2012-10-21
Yes, I found this the case in 12.10 after the same error, didn't have to change groups settings ...

---

### Post by faabiioo on 2012-11-30
Hi, I've been following every single instruction I've found concerning the issues related to nvidia drivers on a hybrid graphics (integrated Intel + Nvidia GPU) with ubuntu 12.10. I've installed and removed bumblebee and executed all related operations. 
All I got eventually is that the card is properly recognised (with driver installed). 
```

lspci -vnn | grep '\''[030[02]\]'
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1140] (rev a1)

```
But no way to execute the "famous" test
```
$ optirun glxspheres 
```
Keep getting
```

[ERROR]You've no permission to communicate with the Bumblebee daemon. Try adding yourself to the 'bumblebee' group
[ERROR]Could not connect to bumblebee daemon - is it running?

```
Tried all the possible solutions found on this and other forums without success.
But, this was with kernel 3.5.0-19-generic updated just this morning. With this kernel, after executing all the instructions for bumblebee and bumblebee-nvidia, bbswitch, linux-headers-generic, etc. I realized that my audio was gone, together with the touchpad: not working anymore.

So I reboot, run ubuntu with kernel 3.5.0-17-generic, and touchpad and audio are back, nvidia device and Intel device are still there, but bumblebee and bbswitch are no longer found. And of course optirun says
```

[ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[ERROR]Aborting because fallback start is disabled.

```

Shall I give up? If I want to use kernel 3.5.0-19-generic, do I need to install linux-headers-3.5.0-19-generic, in order to have bbswitch and bumblebee up and running without compromising other devices?

---

### Post by baobab33 on 2012-12-09
I've got exactly the same problem on my brand new Toshiba P870-319...

No clue on what to do next.

---

