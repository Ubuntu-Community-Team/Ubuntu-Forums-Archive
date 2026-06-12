---
title: "Installation help"
date: 2019-02-25
forum: MINT
---

### Post by ravensm on 2019-02-25
I have installed mint as the only os but it won't boot

Reboot and select proper boot device

1 Mb went to bios reserved
8 Gb to swap
And the rest to root
What did I do wrong?

I tried to use boot repair but it didn't work
[http://paste.ubuntu.com/p/2nyShrbYC5/](http://paste.ubuntu.com/p/2nyShrbYC5/)

I've tried on the mint forums but no one is replying and since mint is based off of ubuntu, I thought someone here could help

---

### Post by wildmanne39 on 2019-02-25
*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by yancek on 2019-02-26
Your boot repair output shows that the computer is an ACER.  If that is correct and it is a newer Acer which came with windows 10 originally, you need to set a Supervisor password in the BIOS and enable trust to be able to install an OS other than windows.  Your output also shows Ubuntu 14.04 on sda3.  Was that a previous install?  It also shows Mint 17 iso which will not have support after April of this year.

---

### Post by ravensm on 2019-02-26
Thank you, yes I'll be upgrading to 19.1 once I get this figured out. As for version 14? I'm not sure where that is came from. Thank you for your suggestion, I'll try it once I get home. As a side note, if I let mint install automaticly instead of choosing 'something else' then it boots just fine

---

### Post by oldfred on 2019-02-26
You have the old BIOS type install, but your system is the newer UEFI hardware.

And  Acer in UEFI boot mode needs the "trust", but I do not think that is required with BIOS boot.

       Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141
      [/URL]
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
       Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---

