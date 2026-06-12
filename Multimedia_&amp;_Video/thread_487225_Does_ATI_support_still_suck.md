---
title: "Does ATI support still suck?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Tadpole on 2007-06-28
I bought a super-cheap [_Radeon 9250_](http://www.newegg.com/Product/Product.asp?Item=N82E16814161010) expecting it to be recognized automatically. I can see from a [_thread last year_](http://ubuntuforums.org/showthread.php?t=182537) that others have had problems, so has anything changed since?

I downloaded [_ATI's drivers_](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html) but they didn't even run and I'm not too hot on [_rebuilding them as .deb packages_](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide#Installing_the_new_driver), as I'm fairly new to this.

Should I return it and get an nvidia?

---

### Post by joe.turion64x2 on 2007-06-28
> **Tadpole said:**
> I bought a super-cheap [_Radeon 9250_](http://www.newegg.com/Product/Product.asp?Item=N82E16814161010) expecting it to be recognized automatically. I can see from a [_thread last year_](http://ubuntuforums.org/showthread.php?t=182537) that others have had problems, so has anything changed since?

I downloaded [_ATI's drivers_](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html) but they didn't even run and I'm not too hot on [_rebuilding them as .deb packages_](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide#Installing_the_new_driver), as I'm fairly new to this.

Should I return it and get an nvidia?
I'd change it, specially if I'd like to use Beryl. It works better in NVIDIA cards. You who have the opportunity (are not stuck in a laptop)...make the switch.

---

### Post by CarpKing on 2007-06-28
From threads I've encountered, that card seems to have particularly bad support.  My 9600 works fine, with either the open-source drivers or ATI's own.

---

### Post by Tadpole on 2007-06-28
I can't even get a signal when I plug my monitor into it. Only the on-board graphics work. Is there a setting in the BIOS I need to change or something?

---

### Post by blackspyder on 2007-06-28
My 9250 from Wal-Mart works fine for me, but then again I dont use desktop effects. It was recognized when I Installed Ubuntu on my PC.

---

### Post by Tadpole on 2007-06-28
> **Tadpole said:**
> I can't even get a signal when I plug my monitor into it. Only the on-board graphics work. Is there a setting in the BIOS I need to change or something?

Wow, I guess I was right! I changed a setting to make PCI the primary graphics adapter and it is now working when I plug it into my graphics card. Only problem now is that it is showing the blue screen of death thing ("Failed to start the X server...").

---

### Post by Tadpole on 2007-06-28
> **blackspyder said:**
> My 9250 from Wal-Mart works fine for me, but then again I dont use desktop effects. It was recognized when I Installed Ubuntu on my PC.

Are you using Feisty? I'm trying to boot my ubuntu cd in safe graphics mode with my monitor plugged into my 9250 and I'm getting the blue screen saying that it failed to start the X server.

---

### Post by jondecker76 on 2007-06-28
I have the 9250 and still can't get things to work correctly (I have 3 other computers with NVidia cards with no problems at all though)

With the 9250, i have been able to get it to work with the open-source ati driver, but not the binary driver so its pretty much useless for games or anything graphically intense (though it will run the basic desktop effects)

---

### Post by Tadpole on 2007-06-28
I just now also tried the [BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) in which you do the following...

```
sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager
```

But when I go to Restricted Drivers Manager it says that my hardware doesn't need any restricted drivers, so there's no way to select "ATI accelerated graphics driver." I'm currently using onboard video, of course, since my card isn't working.

---

### Post by The Afterdark on 2007-06-28
I have an ATI X800 Pro, and I used 7.04 Desktop CD to install (graphically, mind you).  Worked just fine.  Desktop effects worked too.  I then made the mistake of trying to install fglrx drivers, which crippled my system's graphical capabilities (i not longer can use Desktop Effects).

I did try to install 6.10 LTS with the same X800 Pro, and it gave me that same error about "failed to start X Server."

P.S.  If anyone can help me with the crippled graphics, that would be just great.  For more information on the problem, see the following: [http://ubuntuforums.org/showpost.php?p=2896180&postcount=409](http://ubuntuforums.org/showpost.php?p=2896180&postcount=409)

---

### Post by jondecker76 on 2007-06-29
the binary fglrx driver dropped support for cards older than 9500 quite some time ago - so the binary driver simply will not work with the 9250 as it is now considered legacy by ATI. If you look around though, there are tutorials on how to compile the last version of the ATI binary driver that worked with these cards (v8.28.8). HOwever, this is neither fun, nor easy :(

---

### Post by paulg on 2007-06-29
Interesting. I have an x800pro and had the ATI binaries working at one point under 6.10. Didn't have any luck in Feisty. I'm currently using the 'restricted modules' driver. I guess it gets the job done but no testing Beryl for me (mmm... eye candy). 

I guess we'll start to see in the fall if AMD/ATI's announced 'reaffirmation' to open source was blowing smoke or a true commitment. A new driver every month is a big deal (the NVidia drivers are definitely more robust at this point but they're not refreshing every month) so hopefully we'll start seeing some big improvements and eventually some actual open drivers. I doubt their performance will over-take NVidia any time soon but I am hopeful.

---

