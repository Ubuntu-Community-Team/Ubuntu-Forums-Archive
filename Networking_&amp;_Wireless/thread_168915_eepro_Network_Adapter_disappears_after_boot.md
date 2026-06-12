---
title: "eepro Network Adapter disappears after boot"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by binneypl on 2006-05-01
I'm trying to get an old Dell PC with an Intel EtherExpress PRO/10 ISA network card going.
Once I've logged in, I can get the network going fine using: [FONT="Courier New"]modprobe eepro io=0x210 irq=10[/FONT]
(and then enabling the adapter).
But, when I reboot the adapter is no longer present.
/var/log/messages lines include:
[FONT="Courier New"]   isapnp: Card 'Intel EtherExpress(TM) PRO Adapter'
   ... 
   eepro_init_module: Probe is very dangerous in ISA boards!
   eepro_init_module: Please add "autodetect=1" to force probe[/FONT]
After reading other similar posts, I've checked that /etc/modules contains the line:
   [FONT="Courier New"]eepro
[/FONT]
and that /etc/network/interfaces contains the two lines:
[FONT="Courier New"]   auto eth0
   iface eth0 inet dhcp[/FONT]

Do I need to do to add the "autodetect=1" to some other configuration file, please?

---

### Post by binneypl on 2006-05-22
In case anyone else has such an archaic setup, I've worked round my problem by adding the line
> modprobe eepro autodetect=1
to the start section of */etc/init.d/networking*, following the line:
> log_begin_msg "Configuring network interfaces..."

---

### Post by lakosked on 2006-08-04
Unfortunately this solution has not worked for me.  I still have to open a terminal, switch to root, type #sudo modprobe eepro io=0x310 irq 11
then type #ifup eth0

After doing those things I then have network access.  But if I reboot I have to do it again.  I dont know about the isapnp thingy mentioned above so maybe thats it.  Any ideas on how to make this nic work correctly?

---

### Post by lakosked on 2006-08-04
OK problem solved !!!!

I followed this thread and the thread about the etherexpress pro in the Harry? > network   section.

For mine to work I had to edit my etc/modules file.  
I changed
eepro io=310 irq=11
to
eepro io=0x310 irq=11

This made everything work.

---

