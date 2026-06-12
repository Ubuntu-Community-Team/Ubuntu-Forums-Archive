---
title: "Help with ATI Remote Wonder"
date: 2008-05-04
forum: Mythbuntu
---

### Post by scsikid on 2008-05-04
I am using mythbuntu 8.04. This was a fresh install, I have the first generation of ati remote wonder. It worked in older versions of ubuntu with small configuring of lirc. However with mythbuntu 8.04 it appears it is not using the driver.

scsikid@mythtv:~$ lsmod | grep ati
lirc_atiusb            21424  0 
lirc_dev               18248  1 lirc_atiusb
cpufreq_conservative    10632  0 
usbcore               169904  6 lirc_atiusb,rtl8187,usbhid,ehci_hcd,uhci_hcd

lirc_atiusb shows 0

Any tips here, I've searched a lot and tried quite a bit but still stuck at the basics.

---

### Post by superm1 on 2008-05-04
> **scsikid said:**
> I am using mythbuntu 8.04. This was a fresh install, I have the first generation of ati remote wonder. It worked in older versions of ubuntu with small configuring of lirc. However with mythbuntu 8.04 it appears it is not using the driver.

scsikid@mythtv:~$ lsmod | grep ati
lirc_atiusb            21424  0 
lirc_dev               18248  1 lirc_atiusb
cpufreq_conservative    10632  0 
usbcore               169904  6 lirc_atiusb,rtl8187,usbhid,ehci_hcd,uhci_hcd

lirc_atiusb shows 0

Any tips here, I've searched a lot and tried quite a bit but still stuck at the basics.
Check dmesg for any indications that it is being grabbed by a different driver.

Also, make sure it shows up in lsusb.

---

### Post by montgoss on 2008-05-04
I believe I'm having the same problem (no buttons or mouse movements get through)

> **superm1 said:**
> Check dmesg for any indications that it is being grabbed by a different driver.

Also, make sure it shows up in lsusb.

lsusb says:
```
Bus 004 Device 003: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
```

Here is what I believe is the relevant portion of dmesg:
```
[   48.816698] lirc_dev: IR Remote Control driver registered, at major 61 
[   48.834746] 
[   48.834748] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[   48.834751] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   48.848943] lirc_dev: lirc_register_plugin: sample_rate: 0
[   48.868387] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb4:2
[   48.878375] usbcore: registered new interface driver lirc_atiusb
[   48.896601] usbcore: registered new interface driver ati_remote
[   48.896606] /build/buildd/linux-2.6.24/drivers/input/misc/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
```

That seems to me like it detected the remote correctly, no?

---

### Post by CDNdevil on 2008-05-04
I've got the same problem, no response from the irw program either.

---

### Post by newman on 2008-05-05
> **CDNdevil said:**
> I've got the same problem, no response from the irw program either.

I have the exact same issue.  It worked in Gutsy. I've tried blacklisting the lirc_atiusb and ati_remote in modules blacklist. I've also tried installing lirc and reconfiguring it as kernel and also userspace. I'm getting nothing. No responce from irw. It's very frustrating. Hardy seems OK otherwise...

---

### Post by laga on 2008-05-05
Are we talking about this remote? [http://www.mythtv.org/wiki/index.php/Image:Remotewonder1.jpg](http://www.mythtv.org/wiki/index.php/Image:Remotewonder1.jpg)

I've got that one in a drawer somewhere. I'll try to reproduce the problem.

---

### Post by mythpeterp on 2008-05-05
I had to create a symlink to get it to work. 

ln -s /dev/lirc0 /dev/lirc 

Fixed it for me.

---

### Post by newman on 2008-05-06
> **laga said:**
> Are we talking about this remote? [http://www.mythtv.org/wiki/index.php/Image:Remotewonder1.jpg](http://www.mythtv.org/wiki/index.php/Image:Remotewonder1.jpg)

I've got that one in a drawer somewhere. I'll try to reproduce the problem.

Yes, that's the one...

---

### Post by montgoss on 2008-05-06
> **mythpeterp said:**
> I had to create a symlink to get it to work. 

ln -s /dev/lirc0 /dev/lirc 

Fixed it for me.

That didn't seem to do anything for mine.

---

### Post by kringle on 2008-05-06
> **montgoss said:**
> I believe I'm having the same problem (no buttons or mouse movements get through)



lsusb says:
```
Bus 004 Device 003: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
```

Here is what I believe is the relevant portion of dmesg:
```
[   48.816698] lirc_dev: IR Remote Control driver registered, at major 61 
[   48.834746] 
[   48.834748] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[   48.834751] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   48.848943] lirc_dev: lirc_register_plugin: sample_rate: 0
[   48.868387] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb4:2
[   48.878375] usbcore: registered new interface driver lirc_atiusb
[   48.896601] usbcore: registered new interface driver ati_remote
[   48.896606] /build/buildd/linux-2.6.24/drivers/input/misc/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
```

That seems to me like it detected the remote correctly, no?

Any luck?  I'm having the exact same problem--it worked in Gutsy before...

---

### Post by ic_penguin on 2008-05-07
Any updates on this issue? I'm currently waiting to do a switch from Knoppmyth to Mythbuntu until I'm sure I can figure this out.

---

### Post by montgoss on 2008-05-07
I haven't had any luck.  I'm not sure if the others have.

---

### Post by scsikid on 2008-05-08
My apologies, I was away for a few days on vacation, but here are my results after trying all that was suggested.

So it looks like lsusb does show the reciever.
```
scsikid@mythtv:~$ lsusb
Bus 004 Device 006: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
```

I checked dmesg there is nothing showing that it was taken by any other driver.

I noticed that montgoss had the ati_remote module inserted. I based that on his dmesg output. I tried the same as he did. lsmod still looks like the following.

```
root@mythtv:/home/scsikid# lsmod | grep ati
ati_remote             14348  0 
lirc_atiusb            21424  0 
lirc_dev               18248  1 lirc_atiusb
usbcore               169904  7 ati_remote,lirc_atiusb,rtl8187,usbhid,ehci_hcd,uhci_hcd
```

I believe that ati_remote is actually for the 2nd version of the ati remote wonder.

I've tried what newman tried, blacklisting those drivers with no success > **newman said:**
> I have the exact same issue.  It worked in Gutsy. I've tried blacklisting the lirc_atiusb and ati_remote in modules blacklist. I've also tried installing lirc and reconfiguring it as kernel and also userspace. I'm getting nothing. No responce from irw. It's very frustrating. Hardy seems OK otherwise...


Still no luck guys, sorry. I've tried all of this, and if I didn't respond to someones comments it means that someone else already did with the same results. 

Let's continue the struggle!

---

### Post by scsikid on 2008-05-08
Ok guys, think I got it figured out. First I backed up the following. 
```
cp /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb.bak
```

Then I did the following.
```
rm /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb
```

Then add the the following into a new file similar to the one you just deleted.
```
echo '# Please make this file available to others
# by sending it to <lirc at bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0-CVS(atiusb) on Sat Jun 19 16:27:14 2004
#
# contributed by gLaNDix
#
# brand: ATI
# model no. of remote control: 5000023600
# devices being controlled by this remote: MythTV 0.14
#
# USB ID: 0bc7:0004
#

begin remote

   name           REMOTE_WONDER
   bits           16
   eps            30
   aeps          100

   one             0     0
   zero            0     0
   pre_data_bits   8
   pre_data       0x14
   post_data_bits  16
   post_data      0x0
   gap          227933
   toggle_bit      0


       begin codes
           A                        0x000000000000D500
           B                        0x000000000000D601
           C                        0x000000000000EE19
           D                        0x000000000000F01B
           E                        0x000000000000F621
           F                        0x000000000000F823
           POWER                    0x000000000000D702
           TV                       0x000000000000D803
           DVD                      0x000000000000D904
           WEB                      0x000000000000DA05
           BOOK                  0x000000000000DB06
           HAND                     0x000000000000DC07
           MOUSE_LEFT_BTN		  0x0000000000004D78
           MOUSE_LEFTBUTTONUP       0x0000000000004E79
           MOUSE_LEFTBUTTONDBLCLICK 0x0000000000004E79
           MOUSE_RIGHT_BTN          0x000000000000517C
           MOUSE_RIGHTBUTTONUP      0x000000000000527D
           MOUSE_RIGHTBUTTONDBLCLICK 0x000000000000537E
           MOUSE_LEFT               0x0000000000004570
           MOUSE_RIGHT              0x0000000000004671
           MOUSE_UP                 0x0000000000004772
           MOUSE_DOWN               0x0000000000004873
           MOUSE_UPRIGHT            0x0000000000004A75
           MOUSE_DOWNRIGHT          0x0000000000004B76
           MOUSE_DOWNLEFT           0x0000000000004C77
           MOUSE_UPLEFT             0x0000000000004974
           VOL_UP                   0x000000000000DD08
           VOL_DOWN                 0x000000000000DE09
           MUTE                     0x000000000000DF0A
           CH_DOWN                    0x000000000000E10C
           CH_UP                  0x000000000000E00B
           1                        0x000000000000E20D
           2                        0x000000000000E30E
           3                        0x000000000000E40F
           4                        0x000000000000E510
           5                        0x000000000000E611
           6                        0x000000000000E712
           7                        0x000000000000E813
           8                        0x000000000000E914
           9                        0x000000000000EA15
           0                        0x000000000000EC17
           DVD_ROOTMENU             0x000000000000EB16
           SETUP                    0x000000000000ED18
           ARROW_UP                 0x000000000000EF1A
           ARROW_RIGHT              0x000000000000F41F
           ARROW_DOWN               0x000000000000F722
           ARROW_LEFT               0x000000000000F21D
           OK                       0x000000000000F31E
           MAXAMIZE                 0x000000000000F520
           TV_ON_DEMAND             0x000000000000F11C
           BACK                     0x000000000000F924
           PLAY                     0x000000000000FA25
           NEXT                     0x000000000000FB26
           RECORD                   0x000000000000FC27
           STOP                     0x000000000000FD28
           PAUSE                    0x000000000000FE29
       end codes

end remote' > /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb
```

restart lirc
```
/etc/init.d/lirc restart
```

Now try irw and you should get what I got when pressing buttons on the remote.
```
root@mythtv:/etc# irw
00000014e20d0000 00 1 REMOTE_WONDER
00000014e20d0000 01 1 REMOTE_WONDER
00000014e30e0000 00 2 REMOTE_WONDER
00000014e30e0000 01 2 REMOTE_WONDER
```

Once I check that this works with MythTV I will mark it as solved. At the moment I am out of time.

FYI I found that information for the echo'd portion at [http://mikenet.iwarp.com/MythTV/ATI_Remote_Wonder/lircd.conf.TXT](http://mikenet.iwarp.com/MythTV/ATI_Remote_Wonder/lircd.conf.TXT)

---

### Post by montgoss on 2008-05-08
I repeated your steps, but I get nothing when I run irw.

The key difference is probably that "lsmod | grep ati" doesn't have anything like your output.  It contains one line that has nothing to do with ati (cpu_freq_conservative).

---

### Post by scsikid on 2008-05-08
Did you remote that ati_remote module you had inserted before? I think I read somewhere that it conflicts with the older remote's module.

---

### Post by montgoss on 2008-05-08
> **scsikid said:**
> Did you remote that ati_remote module you had inserted before? I think I read somewhere that it conflicts with the older remote's module.

I don't think I ever added an ati_remote module.  You're gonna have to be more specific, cause I don't see anything in this thread that's obviously about that.

---

### Post by scsikid on 2008-05-08
Sorry that was something else I read that someone was trying to do.

Did you have /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb to begin with? Are you running the latest version of ubuntu?

---

### Post by montgoss on 2008-05-08
> **scsikid said:**
> Did you have /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb to begin with? Are you running the latest version of ubuntu?

Yes and yes.

_[This page]("http://epologetics.org/ubuntuhowto.php#remotewonder")_ said to add "ati_remote" to /etc/modules and add "blacklist lirc_atiusb" to /etc/modprobe.d/blacklist.  Is that what you were talking about?  Cause that worked.  Now everything works like it did in the previous version of Ubuntu.  :)

---

### Post by kringle on 2008-05-08
> **montgoss said:**
> Yes and yes.

_[This page]("http://epologetics.org/ubuntuhowto.php#remotewonder")_ said to add "ati_remote" to /etc/modules and add "blacklist lirc_atiusb" to /etc/modprobe.d/blacklist.  Is that what you were talking about?  Cause that worked.  Now everything works like it did in the previous version of Ubuntu.  :)

Thanks Montgoss!  Your directions worked on Hardy Heron for me.  Now, I just have to figure out how to map the keys to do more than move the mouse and raise and lower the volume (although that is a huge improvement).

---

### Post by CDNdevil on 2008-05-08
Ok so using the montgoss way I was also able to use the remote as a mouse and keyboard but doesn't work the way I need, but better then nothing.
I tried scsikid's way and lirc seg faulted 
[   47.062955] lirc_atiusb: USB remote driver for LIRC $Revision: 1.66 $
[   47.062958] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   47.076582] lirc_dev: lirc_register_plugin: sample_rate: 0
[   47.111617] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb1:2
[   47.116942] usbcore: registered new interface driver lirc_atiusb
[  124.205949] lircd[6716]: segfault at 000000f3 eip 08050500 esp bfc2a660 error 4
[  125.443382] lircd[6772]: segfault at 000000f3 eip 08050500 esp bfead8e0 error 4

But we are close I can feel it.:guitar:

---

### Post by scsikid on 2008-05-08
> **montgoss said:**
> Yes and yes.

_[This page]("http://epologetics.org/ubuntuhowto.php#remotewonder")_ said to add "ati_remote" to /etc/modules and add "blacklist lirc_atiusb" to /etc/modprobe.d/blacklist.  Is that what you were talking about?  Cause that worked.  Now everything works like it did in the previous version of Ubuntu.  :)

Yep my mistake I got everything backwards. ati_remote is what you want. lirc_atiusb should be blacklisted.

---

### Post by newman on 2008-05-10
I also had it backwards - 


My /etc/modules had "lirc_atiusb" instead of "ati_remote" and

 /etc/modprobe.d/blacklist had blacklisted "ati_remote" insted of 

"blacklist lirc_atiusb"

Thanks a lot guys! It works! Now I just need to get the key mapping correct...

---

### Post by scsikid on 2008-05-10
I'm sure most of our key mappings will be the same. Whoever does one first for mythbuntu post it.

---

### Post by laga on 2008-05-10
Hi,

there's also a bug report in launchpad: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/224009](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/224009)

I'll try the kernel driver next.

*edit:* I've selected the kernel driver when configuring LIRC, but that doesn't work either. I don't have time to go through that config file right now, though.

---

### Post by Weidbrewer on 2008-05-30
> **scsikid said:**
> I'm sure most of our key mappings will be the same. Whoever does one first for mythbuntu post it.

Any update on this?   I have my remote "working," but not well.   I can move through the main menu in Myth, and play videos....but from there, I am very limited.  I can skip, but not FFWD/RW, I can't stop/exit, etc...I've tried changing the key mapping in lircrc, but nothing changes.

Also, I am using the internal player for all videos and recordings rather than xine or mplayer.

---

### Post by Weidbrewer on 2008-06-02
*bump*

---

### Post by jabeez on 2008-06-05
*bumpity*

I got my RW working, but like previous posters, only kinda. So with previous fix do I try a lirc config or does the "fix" bypass lirc? I'm confused, I got it working enough, but there are still alot of useless buttons as of now.

---

### Post by Weidbrewer on 2008-06-05
Glad I'm not along.  I'd given this thread up for dead.   Yeah, just like you, I have a lot of useless buttons.   Pretty much, I've just got the check-mark for play, and the RLUD arrows for moving around.  Frankly, even though all the buttons is the play, I would settle just for an Esc key so that i can stop playback or move backwards from a menu...

---

### Post by jabeez on 2008-06-05
> **Weidbrewer said:**
> Glad I'm not along.  I'd given this thread up for dead.   Yeah, just like you, I have a lot of useless buttons.   Pretty much, I've just got the check-mark for play, and the RLUD arrows for moving around.  Frankly, even though all the buttons is the play, I would settle just for an Esc key so that i can stop playback or move backwards from a menu...

for what its worth, I just went into mythtv setup > edit keys and made "d" (little button right below check-mark) work for escape. it's still not pretty, but I can at least manage. sheesh, the whole reason I went for mythbuntu this time is for the ease of remote installations, which I've had no shortage of troubles with for the last 4 years!! oh well, it is working and other than time it is free and really quite awesome, so cheers devs, I'll just make sure I have a drink handy when I try to get stuff working........:)

---

### Post by Weidbrewer on 2008-06-05
A good thought....but unfortunately, I haven't been able to get ANY key-bindings/changes to work.

---

### Post by jabeez on 2008-06-05
> **Weidbrewer said:**
> A good thought....but unfortunately, I haven't been able to get ANY key-bindings/changes to work.

strange, for me at least, all the little buttons with just letters on them actually input just those letters, so in mythtv you should be able to change things to get those letters to do whatever you wish. still frustrating though, I've been using Kubuntu since Hoary, and for the most part this remote was picked up and at least the main keys worked (volume, mute, etc.) but now only a few work, and not volume, but the "f" button brings up volume control that can be adjusted with the directional buttons??? and whats up with the button to the right of the directionals locking the screen???

---

### Post by Weidbrewer on 2008-06-05
*facepalm*  Oh.  Now I gotcha.  Yeah, I'll give that a whack and see what happens.

Volume works for me...but it's desktop volume, not Myth.

---

