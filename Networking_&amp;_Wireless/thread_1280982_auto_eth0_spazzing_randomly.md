---
title: "auto eth0 spazzing randomly"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by superwazn on 2009-10-02
at random times i will get disconnected, reconnected, disconnected, reconeccted, just immediately on and off for sometimes up to 15 minutes straight or sometimes it will reconnect and stay on for several minutes before spazzing again. i very much doubt its my internet service because my laptops wireless will work absolutely fine during the time my pc is spazzing. i've looked at a couple of threads and even searched a bit, and while ive seen some similar sounding problems im not sure any of them were quite the same and also none of the fixes suggested helped me. is this my network card?
im using jaunty and i think this thing says my network controller is an intel 82547EI gigabit ethernet controller if that is useful info. thanks for your time helpin me out on this.

---

### Post by kreggz on 2009-10-03
Hi,

Can you open Acessories\Terminal and type dmesg and copy it to [http://pastebin.com/](http://pastebin.com/) ?

---

### Post by ermeyers on 2009-10-03
What's in your /etc/network/interfaces for eth0?  If your using the Ubuntu Desktop Install, there's probably nothing in there except lo, and Network Manager is in control of an Auto eth0 interface.

---

### Post by superwazn on 2009-10-03
this is the output for dmesg [http://pastebin.com/m796f4d0c]("http://pastebin.com/m796f4d0c")
as for whats in /etc/network/interfaces, theres 'auto lo' and also 'iface lo inet loopback'

---

### Post by superwazn on 2009-10-03
update: i think this will sound strange but i have reason now to believe that sites with flash trigger this. i didnt notice it before because i constantly had at least one tab open that had some flash in it, but when i got frustrated and closed firefox, it would stop. i tried firefox a bit later with only one or two tabs open, and the problem wouldnt come back, but as soon as i went to a site running some flash, the problem came back. i honestly dont know how flash would trigger it, but it seems pretty connected.

---

### Post by ermeyers on 2009-10-03
> **superwazn said:**
> this is the output for dmesg [http://pastebin.com/m796f4d0c]("http://pastebin.com/m796f4d0c")
as for whats in /etc/network/interfaces, theres 'auto lo' and also 'iface lo inet loopback'
That's the lo stuff that I said would be in there.  Network Manager is controlling Auto eth0.  A full-time server paradigm would have entries in /etc/network/interfaces like:

...
auto eth0
iface eth0 inet dhcp

---

### Post by superwazn on 2009-10-03
are you suggesting i add those?

---

### Post by kreggz on 2009-10-03
Wow I can see that indeed the eth0 is up and down like a yo yo

Your eth0 is being detected as RTL8139 Realtek

Did you have this same problem on the live disk?

---

### Post by superwazn on 2009-10-03
no, i upgraded from 8.10, and i didnt have this problem with 9.04 until recently, say, the last month or two, with its occurrence frequency increasing.
and when i do System>Administration>System testing the test tells me i have two controllers, the Intel one i originally mentioned and a Realtek one, so that would explain what you noticed. @_@ i used to be good with computers but ubuntu made things so easy i never had to fix anything except once in a blue moon XD

---

### Post by kreggz on 2009-10-04
do you have two nics or is the intel one a realtek chip?

---

### Post by ermeyers on 2009-10-04
> **superwazn said:**
> are you suggesting i add those?
If you want a full-time connection, yes.  If you want to get the Network Manager out of the picture temporarily, yes.  If you want a static connection here's an example.  My eth0 is my LAN, and eth1_rename is my DSL connection that provides a 192.168.1.0 network number.

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address 192.168.0.1
   netmask 255.255.255.0
   network 192.168.0.0
   broadcast 192.168.0.255

auto eth1_rename
iface eth1_rename inet dhcp

---

