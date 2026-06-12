---
title: "backend crashing every 3 or so days"
date: 2009-08-26
forum: Mythbuntu
---

### Post by smckay79 on 2009-08-26
Hey guys,

Wondering if someone can point me in the right direction to solve this issue. I have the latest mythbuntu installed on my backend. Everything is working including my 3 tuners and my firewire cable box, everything seems to be fine. Except:

Every 3 or so days, my backend crashes out on my, if i look at the monitor its connected to the video looks all pixalated and frozen. the only way to fix it is a hard reset - the machine is not pingable or anything. 

I thought heat, but the ambient heat is fine in the case ect. 

Can someone help me try to figure this out - I have access of course to all logs, ect.

Cheers

Scott

---

### Post by ian dobson on 2009-08-27
Hi,

Could you try running memtest (from the grub boot menu) to check your memory.

Maybe after a crash reboot the box and login as root then from the terminal do a dmesg. Maybe linux has written something to the syslog as to what's wrong.

Could you provide abit more information: What hardware is in the backend, are you running X on the backend?

Regards
Ian Dobson

---

### Post by mitchell2345 on 2009-08-28
what video drivers are you using?

~Mitchell

---

### Post by smckay79 on 2009-09-03
I am running the Nvidia 180 drivers, I have a 8600 video card.

The backend is running on an A8N-SLI Premium with a amd 64 fx-57 processor running at 2.8 GHZ

1 gig ram (400 mhz)
2 pvr250s
1pvr 150
1 firewire capture off a dct-6200

I use a commandir usb blaster/receiver.

Everything works fine, but then it dies... the unit is connected to a tv in my basement, if i turn the tv on the video is all pixalated and shifted... kinda like when you knew you had to blow on those old nintendo cartridges.... Nothing is responsive, not pingable, ect. reboot (hit reset) the system comes back, but will die again...

Ill run memtest - i checked the dmesg and nothing stands out, same with the system logs...

---

### Post by williammanda on 2009-09-06
If checking the logs doesn't show anything then the hardware is suspect. 
1. I would check the memory as suggested.
2. Remove the box cover and test it for 3 - 4 days.
3. I would remove as many cards as possible and test for the 3 - 4 days.
4. If there is still the issue, swap out the memory then the motherboard.
Thanks

---

