---
title: "ubuntu 10.10 RC Installer may not burn correctly even with the 697 MB ISOs..."
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Lucradia on 2010-10-02
Well, my CD-RWs are either dying, etc. (even though I've only used them 5 times since I bought them a couple months ago)

or the ISO itself is damaged, and thus cannot install correctly.

The ubuntu installer when run complains that it crashed near almost the end of the copying file section of the installer (after partitions, etc. are placed.) And gives a Disk Read I/O warning as well. it's not the harddrive, I know this because Fedora installed correctly (but couldn't resize the Harddrive, windows had to. But ubuntu resizes fine, but Windows complains of disk continuity.)

Wubi and virtualization are out of the question due to network issues with my Realtek adapter (causing bluescreens with Vbox in Windows 7 when switching from Bridged to NAT.)

nothing would really work on the liveCD after the installer crashed, so I couldn't get the log of the error, sorry. I don't have launchpad, nor am willing to sign up or login to it, so even if I had the log, I'd post it here, not there.

---

### Post by coffeecat on 2010-10-02
> **Lucradia said:**
> or the ISO itself is damaged, and thus cannot install correctly.

Did you check the md5sum hash before using the ISO?

I burnt the downloaded ubuntu-10.10-rc-desktop-amd64.iso file  to a CD-RW and used that to install Maverick to one of my laptops. I didn't experience any problems.

Usual advice. Check the md5sum and burn at a low speed.

---

### Post by Lucradia on 2010-10-02
How do I check the MD5SUM on Windows again? I forgot.

---

### Post by coffeecat on 2010-10-02
> **Lucradia said:**
> How do I check the MD5SUM on Windows again? I forgot.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

Another for your bookmarks:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Includes details of a good free Windows burning app.

---

### Post by Lucradia on 2010-10-02
My burner is Infra Recorder, I've checked the md5sum on a newly downloaded ISO 9it is the same) and am not going to attempt to install it aside Windows 7 once more.

However, I should tell you that my DVD Burner has a speed of 10x, which is its lowest and apparently maximum speed as well, Infra Recorder cannot tell the Burn Drive to go lower than 10x even though that's the burner's max for CD-RW.

---

### Post by coffeecat on 2010-10-02
> **Lucradia said:**
> Infra Recorder cannot tell the Burn Drive to go lower than 10x even though that's the burner's max for CD-RW.

I get that with Brasero in gnome with one machine's optical drive, but I can get x4 with another. Frustrating, I know.

I get variable results with CD-RWs. My Phillips ones seem to go on and on, but some Verbatims (which I thought was a good make) seem to have deteriorated after only a couple of uses.

---

### Post by cariboo on 2010-10-02
On the other hand I've had good luck with Verbatim. Most DVD burners don't pay any attention to the speed you set, it will burn at the speed that the disk is rated for.

The Verbatim CD/RW are only 4X, so I get a good burn every time. 

There have been quite a few changes to Brasero to make it better too, it now creates a checksum before the burn and compares it after the burn, I haven't seen any /dev/sr0 errors in the past week, since the updates.

---

### Post by Lucradia on 2010-10-02
Well it installed, so everything's A-OK now. I just wish the GTX 470 wouldn't lag for a second or two when it switches workspaces with any compiz effect. (but only when I first start using the effect, after I am inside the effect, it no longer lags.)

---

