---
title: "Brother Network printing and I have the drivers!"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Ken UK on 2011-04-30
Hi everyone,

So Im trying to setup my stand alone network printer, a Brother DCP-6690CW and I have found the official page for installation provided by Brother: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2)

I downloaded both parts of the driver but installed them graphically because I find it easier to understand using GDebi package installer.

Now it tells me to edit some file to change it so its configured for Network instead of USB (default). I can't do it graphically (presumably?) because you need root access. What do I do to make the changes I need to make? Does anyone have experience with this, am I doing it correct?

Thanks,

Ken

---

### Post by Ken UK on 2011-04-30
Ok so I figured out how to edit the file through the teminal:

```
sudo gedit /etc/printcap
```

but then I get:
> (gedit:19778): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.UNBMUV': No such file or directory

(gedit:19778): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Could someone please just explain what I need to do. I have the Linux drivers but Im clueless as to what Im suppose to be doing with them, I follow brothers instructions but it doesn’t seem to have done anything :(

---

### Post by Ken UK on 2011-04-30
Hell yeah! Im getting the hang of this Linux thing!

I didn't follow the Brother instructions in the end, I installed the drivers but then added a printer and used the HP JetDirect option along with my printers IP address. Good god man that was so easy if only I knew what I am doing :D

---

