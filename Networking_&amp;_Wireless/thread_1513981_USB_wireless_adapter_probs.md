---
title: "USB wireless adapter probs"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by scarritr on 2010-06-20
I am pretty much brand new at this, so be gentle, guys.  I installed Ubuntu 10.04, restarted with the USB adapter attached, and it must have been installed automatically because, voila, the next thing I knew I was connected. 

However, that was short lived.  The next time I booted, no internet connection, and, although the little green light is on in the adapter, it is clearly not recognized.  If I boot with the adapter plugged in, I get the green light  ...  if I unplug it and then plug it back in, the green light is off and there is no sign of it being recognized.

The adapter is a garden variety TrendNet TEW 444UB.

So, it installed and connected once, so one might think the requisite drivers are there.  How do I trigger a connection or re-installation ?  

Again, be gentle  ...  please explain carefully and fully.

Thanks much.  I really appreciate it !

Richard in KC

---

### Post by cariboo on 2010-06-20
To do some trouble shooting, you need to open an Applications->Accessories->Termianl. To check if your device is detected properly at the prompt in the terminal type:

```
dmesg | tail -n10
```

just after you plugged your device in, paste the results in your next post.

You didn't say how you were posting, so just in case you are doing it from Windows, you can modify the above command to create a text file that you can copy to your Windows partition:

```
dmesg | tail -n10 > dmesg.txt
```

The above command will create a text file in your home directory called dmesg.txt.

---

### Post by scarritr on 2010-06-20
Here is the text file I saved of the results of the command you gave me to run.  

I am running between two floors between a Windows machine and the Ubunto machine.

When you respond (I hope I haven't lost you), please also tell me how to get to the equivalent of Windows Explorer in Ubuntu.

Many Thanks

RWSinKC

---

### Post by cariboo on 2010-06-21
It looks like your device isn't being detected at all. Checking the manufacturers web site, your device isn't supported. You may be able to get it to work using ndiswrapper. Have a look at the [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") wiki page.

---

### Post by scarritr on 2010-06-21
[[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104"),  thanks !

1)  Strange, inasmuch as it did work and I was connected the first time;

2)  What does one check for on the mfgr's web site ? 

Again, thanks

Richard in  KC

---

