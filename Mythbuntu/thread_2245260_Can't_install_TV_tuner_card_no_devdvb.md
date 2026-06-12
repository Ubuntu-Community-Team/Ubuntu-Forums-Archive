---
title: "Can't install TV tuner card: no /dev/dvb"
date: 2014-09-22
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2014-09-22
I have just set up an oldish system with new hard disks, a new install of Ubuntu 14.04 and MythTV 0.27, and a new TV tuner card. The TV tuner card is a TBS6285.

I have followed the instructions for "making it work" on [this page]("http://www.linuxtv.org/wiki/index.php/TBS6284") (for the closely related TBS6284: the instructions on the TBS6285 page just tell you to follow the TBS6284 instructions), and everything worked just fine up to step 8. I got the messages from the syslog and dmesg exactly as the page described.

However, when I tried the next bit:

```
ls -al /dev/dvb 
```

I am told there is no such directory as /dev/dvb (which indeed there isn't).

I'm a bit stumped about what to do next. Any ideas?

---

### Post by Gillingham on 2014-09-22
With my TBS6220 card on my upgrade to 14.04 and subsequent re-installations I have had to manually run an extra command
```
sudo rm -R /lib/modules/3.13.0-24-generic/kernel//drivers/media/
```
as the first thing I do replacing "3.13.0-24-generic" with the current kernel version.  If this is the case you would need to run ```
make distclean
```
and restart at item 5.

This step will probably be needed when you upgrade the kernel.

David

---

### Post by Adam_Jacobs on 2014-09-23
Thanks for that suggestion, David. Sadly, no dice. I did as you suggested and deleted the media drivers folder, then ran through the installation steps again, but with the same result. Everything behaves exactly as expected right up to half way through step 8, where I get the expected messages in syslog and dmesg, but /dev/dvb remains stubbornly non-existent.

I have googled extensively for this. There are many problems with installing this card, but the precise problem I'm having doesn't seem to be described anywhere as far as I can tell. I'm beginning to think I may have to send the card back for a refund. :(

---

### Post by Adam_Jacobs on 2014-09-23
I'm happy to say I solved this one, with the aid of a very helpful chap from TBS technical support.

It turns out my card was from a faulty batch that had an incorrect hardware ID number programmed into it. It was a bit faffy to correct this: it involved taking the card out, putting it in a Windows machine, and running a little software tool, but at the end of all that, it seems to work.

If anyone else has the same problem, the instructions for fixing it are [here]("http://www.tbsdtv.com/forum/viewtopic.php?f=153&t=8698").

---

