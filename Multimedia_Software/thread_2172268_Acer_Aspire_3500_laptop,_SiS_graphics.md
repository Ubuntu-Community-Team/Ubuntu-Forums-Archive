---
title: "Acer Aspire 3500 laptop, SiS graphics"
date: 2013-09-04
forum: Multimedia Software
---

### Post by ptT7rLC on 2013-09-04
Hi 

I am attempting to install ubuntu on an Acer Aspire 3500.  It could not detect the video so is running in low resolution.  As new to Linux (old command line Xenix guy) any pointers or clues?  I have it at the install screen it stopped at.

Cheers

---

### Post by mörgæs on 2013-09-04
Hi, welcome to the fora.

It's likely a problem with SiS graphics. Please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by ptT7rLC on 2013-09-04
Hi and thanks. 

I am on the install from DVD phase and stuck on the low resolution screen with limited options. When I tried the command line all I got was the text that I typed and no reply.  Control alt resulted in a shutdown so the machine did not lock just does do nothing. 

Restarted install and it is now it is doing its half hour of flashing screen trick before it figures out it does not like the video card. 

Ok come up with "The system is running in low-graphics mode". Hit enter and have four options.  First is "run in low graphics mode" but failed along with the last being exit to console login.  

What is the next step?
 
Cheers

---

### Post by ptT7rLC on 2013-09-04
Hang on got to the cmd line.  Did as you said but no way to copy file as at very early install phase.  Vi the file and the display is Silicon Intergrated Sytems.  

Product 661/741/760 PCI/AGP or 662/761Gx PCIE VGA adapter. 

Any help?

---

### Post by Bucky Ball on 2013-09-04
*Thread moved to **Multimedia & Video**.*

Welcome to the forums. More appropriate here and you may have more luck.

Just a tip. Please use descriptive titles for threads. This will increase your chances of help. Generic ones like the one here give no information about the issue you're having. 

Good luck.

PS: morgaes may be able to provide more info, but would the 'nomodset' option be of any help here? If you are getting to the screen when installing that gives you the option to try Ubuntu or install, hit F6, choose 'nomodset' and continue. This might get you to something workable if nothing else.

---

### Post by mörgæs on 2013-09-04
Have added the 'SiS' information to the title.

My only idea is 

```
sudo apt-get remove xserver-xorg-video-sis
```

if you can get to a terminal, as suggested in 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1034812/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1034812/)

If that does not work I would try Bodhi Linux, because it is based upon 12.04. There's a link in my signature.

I don't know if boot options help.

---

### Post by ptT7rLC on 2013-09-04
Hi

I have downloaded bohi-2.3.0-32 and will give that a try.  Also will run your command line code as the computer it did come up with a shell.  

I am a mad keen OSM mapper and been using Windows but it is rather a pain to do things as you wind up doing them manually so thought I would try Linux.  Maybe the old laptop is not up to the task but it would be a shame to junk it as it works well   Is there any affordable laptops that I can pickup cheap from Ebay that Linux will run well on?
 
Many year ago I tried Linux but always got trapped by hardware issues rather hoping that things have improved.

Cheers

---

### Post by ptT7rLC on 2013-09-05
Hi 

Used Bohi Lunix and the result was initially good with install going smoothly then the screen started the flickering and went blank.  Shut it down using the cntl alt sequence and rebooted.  It would come up sometimes but other times would not. 

Have not quite worked out what happens with the function keys I hit.  But this seems to get the screen to display.  New to this so it could be just time needed to work. 

Now with the sudo removal of the SIS graphic feature can I still use programs like graphical mapping ones?  I do not mind giving away speed as all they do is display maps. Also can I use the Open Office programs?  Basically what effect is the removal of SIS going to have?  As mentioned I can live with slower screen updates. 

I am attempting yet another reinstall having removed SIS the external monitor port would not work. 

Thanks for your help.  We are almost there as I appear to be able to have a running system but with monitor issues. 

Cheers

---

### Post by ptT7rLC on 2013-09-05
Ok curious issues. 

When I did the install with an external monitor connected to the laptop it went right through with a clean install. 

The laptop screen is 1200x800 native.  But remove the screen and it works until shutdown and reboot then blank screen. Reattach the monitor and using F7 the screen will come up on a reboot.   The external monitor has a different native resolution to the laptop. 

Ok removed the sis package and the screen on the laptop on reboot comes up as 1024x768 and looks poor as it is not the native resolution but it boots up nicely. 

Tried reboot with external monitor and it came up with the native resolution if 1280x1024 and looks good.  Unplug the monitor and the laptop screen does not come up. 

Ok next step to get the laptop screen to display its native resolution of 1200x800?

Thanks Brett

---

### Post by Yellow Pasque on 2013-09-05
Reinstall the xserver-xorg-video-sis package and create an /etc/X11/xorg.conf file with the following contents:
```

Section "Device"
        Identifier "Configured Video Device"
        Option "NoAccel" "true"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection
```

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)

---

### Post by mörgæs on 2013-09-05
Thanks for dropping by, Temüjin. 


There seems to be some confusion about xserver-xorg-video-sis (at least I am). When should it be removed and when should it be configured through xorg.conf?

---

### Post by Yellow Pasque on 2013-09-05
Most users will want it removed (especially if they can't start X :P ). The main benefit of having it installed is to get some resolutions not supported by the generic VESA driver (like 1280x800).

The only way users will get 2D acceleration from the SiS driver is by using Ubuntu 12.04.1 (and not installing the -LTS X packages).

---

### Post by mörgæs on 2013-09-06
Thanks. Since I can't send you a private messages I have to post here: 

Would it be possible for you to write a brief wiki page describing the SiS problem and solutions/workarounds? It would benefit a lot, both people with a SiS problem and the ones trying to provide an answer.

---

### Post by Yellow Pasque on 2013-09-06
mörgæs, I thought forum staff could PM me (or maybe that's just to discipline me :P ).

Anyway, I'll take a stab at writing or updating the ubuntuwiki SiS page. While I understand the issue and the workarounds, I'm a little foggy on the impact. I marked the bug Critical because users were reporting crashing with the live media, but that doesn't seem to be the case for all SiS users if I understand correctly.

I'll also consider trying to package the upstream patch.

---

### Post by Bucky Ball on 2013-09-06
@Temüjin: Sorry to butt in here, but no-one can PM you. I just tried also and there is no option to private message.

You are looking for this:

> Receive Private Messages only from Contacts and Moderators

You have it set to 'no'. It should be 'yes'. While we're here, you also have this set to 'no'.

> Receive Admin Emails

Probably not good in light of recent events. Only way to reach you if forum explodes again. ;)

* Sincere apologies to OP about off-topic interruption. Only way to convey this information to user at the mo. Thnks for your understanding.  As you were! ;)

---

### Post by ptT7rLC on 2013-09-06
Hi People

Thanks for the information.  Everything is a learning process for me but I figured out the internet connection to install sis and this actually worked without the xconfig file.  But as I was on a roll I started the browser and cut the code and attempted to create the file.  It has been two decades since I last used vi so that was an experience but then it would not save and su gave wrong password?  Bit more research and I used sudo bash and that worked.    Rather different version of Linux/Unix and surprised when the lc was not installed.  Talk about a lean version of Linux!!!

So I now have a screen working in 1280x800 and a laptop that boots up with no issues.  Now the serious learning starts, like how can I get su to work.  And why does Microsoft Live not work with the browser (ok they are evil and probably blocked non Window machines).

Next trick is memory hunting to bring the Acer up to 2GB from 512mb.

Anyway, thanks for your help and patience and be great if you can get the sis issue nailed for other users.  Much appreciated are your efforts.  Now back to OSM mapping.

Cheers and thanks again from Brett

---

### Post by Bucky Ball on 2013-09-06
Great news, ptT7rLC. Could you please mark thread as solved (if it is to your satisfaction) from Thread Tools at top right? That will be of help to others for starters. ;)

PS: Apologies again about interruption.

---

### Post by Yellow Pasque on 2013-09-06
>  It has been two decades since I last used vi so that was an experience but then it would not save and su gave wrong password?
```
gksu gedit <file>
```

> like how can I get su to work.
It's possible, but highly discouraged on buntu. Use 'sudo bash' or 'sudo -i' instead: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

