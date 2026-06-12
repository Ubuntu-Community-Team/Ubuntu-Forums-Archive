---
title: "Video Driver for Ubuntu 12.04"
date: 2012-05-11
forum: Multimedia Software
---

### Post by felipeabrao on 2012-05-11
Hello, all,

would you know any video driver for Ubuntu 12.04, for a 32 bit Dell computer? My video is very low, and there are frequent problems with the image on the monitor. And how do I get this drive?

Thank you in advance,

Felipe

---

### Post by DELL JonathanS on 2012-05-11
Hello Felipe,
 
I work for Dell and I wanted to see if I could assist. What is the model of your Dell computer? Many Dell models work well under Ubuntu with some configuration, though Ubuntu also does a lot of very helpful and correct autoconfiguration. Also could you please paste the output of the lspci -n command so we can identify the hardware in question and recommend a suitable driver? Finally, what sort of image problems are you seeing? Some types of image problems can be caused by using an incorrect driver, misconfigured monitor settings, or possibly a faulty video chipset or cable. Let me know and I'll try to help.
 
Thanks,
Jonathan S.

---

### Post by felipeabrao on 2012-05-12
Hello, Jonathan,

first of all I would like to thank you very much for your support. Well, the model of my Dell computer is Optiplex 740 Enhanced, with AMD Athlon(tm) Dual Core Processor 5400B × 2. The output of the lspci -n command is

```

00:00.0 0500: 10de:02f0 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:04.0 0604: 10de:02fb (rev a1)
00:05.0 0300: 10de:0241 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0260 (rev a3)
00:0a.1 0c05: 10de:0264 (rev a3)
00:0a.2 0500: 10de:0272 (rev a3)
00:0b.0 0c03: 10de:026d (rev a3)
00:0b.1 0c03: 10de:026e (rev a3)
00:0e.0 0101: 10de:0266 (rev a1)
00:0f.0 0101: 10de:0267 (rev a1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
02:00.0 0200: 14e4:167a (rev 02)

``` 

The problems I have experienced are: video blocking (nothing moves, nor even the mouse pointer, and I have to reboot the computer), some images become suddenly a splodge and/or move very slow (especially when I minimize or maximize a window). I tried the Nvidia acceleration video driver, but everything became black, and I uninstalled it. Thank you,

Felipe

---

### Post by DELL JonathanS on 2012-05-14
[FONT=Calibri]My reply:[/FONT]
  > 
  ```

  [COLOR=black][FONT=Verdana]00:05.0 0300: 10de:0241 (rev a2)[/FONT][/COLOR]
  
```
  
  [COLOR=black][FONT=Verdana]The problems I have experienced are: video blocking (nothing moves, nor even the mouse pointer, and I have to reboot the computer), some images become suddenly a splodge and/or move very slow (especially when I minimize or maximize a window). I tried the Nvidia acceleration video driver, but everything became black, and I uninstalled it. Thank you,[/FONT][/COLOR]
  
  [COLOR=black][FONT=Verdana]Felipe[/FONT][/COLOR]
  
  [FONT=Verdana][COLOR=black]Thanks for the update Felipe. It looks like you have the GeForce 6150 LE (10DE:0241). Is the system stable booting into single user mode (i.e. without GUI)? I wonder if this pertains to your issue: [/COLOR][http://askubuntu.com/a/130209](http://askubuntu.com/a/130209)[COLOR=black] -- Does the issue persist when you install nvidia-current? Or is that what you meant by Nvidia acceleration video driver, just to clarify? Also, have you had this issue on previous Ubuntu releases or is this the first time you have tried it?[/COLOR][/FONT]

---

### Post by jawilljr on 2012-05-14
The driver in in additional-drivers is 295.40...which has a lot of bugs.

I would try Nvidia version 295.49 which is available in the x-swat PPA. Just run the below commands in the terminal:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get nvidia-current
```

Hope this helps.

Jerry

---

### Post by felipeabrao on 2012-05-24
Thank you, Jonathan and Jerry!

I am sorry for the late reply. I followed the suggestion of Jerry, but the last command

```
sudo apt-get nvidia-current
```

did not work. Anyway, I downloaded the package nvidia-current-dev295.53-0ubuntu1~precise~xup1 from the website of Ubuntu-X and now my video is excellent. Thank you all very much!

Felipe

---

