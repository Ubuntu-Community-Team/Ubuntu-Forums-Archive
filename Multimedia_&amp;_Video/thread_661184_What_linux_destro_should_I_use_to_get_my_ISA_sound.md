---
title: "What linux destro should I use to get my ISA sound card working."
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by knw on 2008-01-07
I got a P3 733mhz 512 ram rig

Trying to run Linux on it only to access the web with Flash support and sound nothing else is needed on this machine.

This machine will only access 1 web site with a flash training application running on it...users using this machine will only need to access this web site to a traning course witch requires for them to listen.

This machine is fine except the  Creative Labs Sound Blaster AWE64 ISA Sound Card (CT4520) in it won't get detected by ubuntu...and it was working fine under WindowsME pre Ubuntu installation.

Now I'm just wondering what destro would make this card working from the start...even older installations of any destro will do that will have a browser that will support flash and HAVE SOUND.

I've spend more then 2 days on this...any help would be appreciated!!

BTW I'v tried to modprobe the card but no luck I'll read a lot of howto's on this.

Should I try Xubuntu 6.06.1??

Thanks

---

### Post by kwacka on 2008-01-07
Is the card mentioned in dmesg at all?

---

### Post by wolfen69 on 2008-01-07
try Puppy Linux.

---

### Post by AlexEagar on 2008-02-16
Use Ubuntu.

[Solution Source]("http://ubuntuforums.org/archive/index.php/t-115697.html")
[Explanation]("http://www.osnews.com/permalink?f298700")

Add the following line to /etc/modules and then reboot.

snd-sbawe

---

### Post by rafalmag on 2008-07-07
> **AlexEagar said:**
> 

Add the following line to /etc/modules and then reboot.

snd-sbawe

Thank you for reply. I have the same ISA soundcard and it runs now like a charm.

I read about some pnp and irq settings and it was just simple.

Thank you.

---

