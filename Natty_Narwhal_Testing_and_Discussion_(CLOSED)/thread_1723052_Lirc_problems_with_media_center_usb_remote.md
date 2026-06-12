---
title: "Lirc problems with media center usb remote"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by druhboruch on 2011-04-06
On new installation of natty remote sends double keypresses.
It worked fine with maverick.

To fix it I have to run following manually after each boot:

```
modprobe -r rc_rc6_mce
modprobe -r ir_rc5_decoder
modprobe -r ir_rc6_decoder

```

Blacklisting these modules has no effect.  They are being loaded anyways.

Could you give me any suggestion on how to fix it?

---

### Post by druhboruch on 2011-04-07
Hi everyone,
I am hoping for any hint or suggestion...

I found out after some searching that the module for media center remote is now included in the natty's kernel.  

I would like to understand why blacklisted modules are beeing loaded and how to prevent it from happening.

---

### Post by cariboo on 2011-04-07
What does the blacklist file you created look like?

---

### Post by druhboruch on 2011-04-07
Thank you for replying cariboo907.

I added 3 lines at the end of /etc/modprobe.d/blacklist.conf

```
blacklist rc_rc6_mce
blacklist ir_rc5_decoder
blacklist ir_rc6_decoder
```

I think this is the proper way to do it...

---

### Post by druhboruch on 2011-04-10
Anyone?

---

### Post by bdagerman on 2011-04-21
I am having this problem too. I am running Mythbuntu 11.04 beta 2, and my MCE remote keeps repeating the input for the arrow keys.

Per the OP and [the mythTV MCE wiki]("http://www.mythtv.org/wiki/MCE_Remote#Arrow_Buttons_Repeat") running 
```
modprobe -r ir_rc6_decoder
```
fixes the problem. However, like the OP, when I try to blacklist the module in /etc/modprobe.d/blacklist.conf, it still loads the module on reboot.

---

### Post by bootc on 2011-04-23
The correct fix for this in Natty is this:

```
echo lirc > /sys/class/rc/rc0/protocols
```Just add that line to /etc/rc.local and it will be done at boot. Blacklisting the modules doesn't work because they're loaded in from inside the kernel.

---

### Post by malcolm-t on 2011-04-23
fantastic, that fixed it for me.

---

