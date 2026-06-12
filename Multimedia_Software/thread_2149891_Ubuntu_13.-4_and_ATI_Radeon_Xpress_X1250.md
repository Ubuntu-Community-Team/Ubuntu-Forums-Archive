---
title: "Ubuntu 13.-4 and ATI Radeon Xpress X1250"
date: 2013-05-30
forum: Multimedia Software
---

### Post by jesus-freak on 2013-05-30
I have two Toshiba Laptops. I installed Ubuntu 13.04 on my laptop and it works flawlessly. I loved it so much that I decided to install it on my wifes Toshiba Satellite A305D-S6848. I installed it fine but after install I noticed two things, the first thing was that it seems to lag and not be very snappy like my other laptop (which is only slightly higher specs). The next thing I noticed was that when I opened the dash the page looked all scrambled up. After researching this I found out that problem was due to the blur option being turned on. I turned it off and now the dash looks find but is still quite slow to open up. The entire system seems slow. Now, this computer came with the bloated windows vista and it ran that beast with all the effect on without any problem so I find it hard to believe that the system can't handle unbuntu 13.04. I have turned off extra effects, changed the swappiness value, the basic stuff they say to do to try to get better performance but I have not had any luck making it work faster. So now I'm thinking it has something to do with the graphics card and the compatibility in between my card and Ubuntu. By default Ubuntu installed "Gallium 0.4 on ATI RS690.

Here are the specs on the computer.

Processor 	2.0GHz AMD Turion 64 X2 TL-60
Memory 	3GB at 667MHz DDR2
Hard drive 	200GB at 5,400rpm
Chipset 	ATI RS690M
Graphics 	ATI Radeon Xpress X1250 (integrated)

I found some sites and they are saying that when using an older ATI graphics card that you want to do the following...

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy

But that was a fix made for Ubuntu 12.10. Would I follow the same procedure for 13.04?.

Thanks for any help

Justin

---

### Post by Cheesemill on 2013-05-30
That fix won't work for your card, it's only for the 2/3/4xxx series of cards that ATI dropped support for last year.

Support for the 1xxx series cards was dropped several years ago, the ***only*** driver that will work with your card is the default radeon driver that is built into the kernel. It's the driver that you are already using.

PS - Even if you did have a 2/3/4xxx series card I would seriously reccomend not following those instructions, it's an ugly hack that downgrades vital parts of the OS and could lead to serious system breakage at any time.

---

### Post by jesus-freak on 2013-05-30
Thanks for the info. Anyone have any ideas on how to make this not so slow? Would an older version of Ubuntu work any better?

---

### Post by Cheesemill on 2013-05-30
You could try 12.04.1 as it still has the Unity 2D session which has been dropped from later releases. Unity 2D is specifically desgned to run on less able graphics hardware.

Another option would be to use 13.04, but to use either Xubutu or Lubuntu as again these are designed for lower spec hardware.

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)
[http://cdimage.ubuntu.com/xubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/13.04/release/)
[http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/)

---

### Post by Yellow Pasque on 2013-05-30
I agree that a non-3D desktop would be best for the X1250 (I used to have one and it was pretty darn slow too).
You don't need to install an entire .iso to try out xfce. Just install the appropriate xfce4 metapackage and then choose xfce when logging in.

---

### Post by Mark Phelps on 2013-05-30
I would second the use of 12.04.  

I used an x1650 years ago with (I think) Ubuntu 11.x and it worked quite well -- with the default drivers.

---

### Post by jesus-freak on 2013-05-31
Thanks everyone for your suggestions!! I also think the best way to go is to downgrade to 12.04 with unity 2D. However, I have another problem. The DVD drive on my wife’s computer is no longer working. I had a REALLY hard time getting 13.04 on there because when I tried to plug in an external DVD drive and boot from the disc it wouldn't let me. There was no option in the bios to boot from any usb devices. After a while a friend of ours tried it and did something and ended up being able to boot from the external DVD drive and installing 13.04. The thing is, I'm an American living in the Philippines so our friend wasn't able to tell me in English how he did this LOL. Anyway, is there any way to downgrade to 12.04 from within 13.04? Like commands that roll back and download needed elements until you are running 12.04? I'm new to Ubuntu and linux in general so forgive me if this is a stupid question.

---

### Post by Yellow Pasque on 2013-05-31
No, you can't downgrade, and there's really no need to (unless you absolutely must have Unity). Try the xfce desktop. It's more traditional than Unity, but it's also much faster.

---

### Post by Mark Phelps on 2013-05-31
>  Anyway, is there any way to downgrade to 12.04 from within 13.04? 

Unfortunately, after all these years, Canonical STILL has not seen fit to incorporate any kind of version Roll-Back capability -- that, if present, could serve to save many a person's system who upgraded, only to run into serious problems.

---

