---
title: "Network connection preference"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by krishnamohan on 2009-12-24
Hi...

I have network manager installed...I have connections named eth0 and eth1...

The connection I generally use is eth1...but after booting the computer goes to eth0 and I have to go and click on eth1 to activate it..


How do I arrange it so that eth1 is connected as the computer starts up?

---

### Post by Iowan on 2009-12-24
Are either/both set to "Connect automatically"? (I presume at least eth0 is) Perhaps as simple as reversing the checkbox options?

---

### Post by krishnamohan on 2009-12-25
Yes..both are set to connect automatically..I do not see how I can reverse the options....is there a file somewhere that I can edit to say go online on this connection at boot/

---

### Post by KeLa on 2009-12-25
Select eth0 and click edit and remove tick from "Connect automatically" checkbox and save settings and reboot.
Then it should work so that only eth1 is connected automatically and then you can manually connect eth0 if you need it.

---

### Post by krishnamohan on 2009-12-25
No..,,I am not able to do that ...the eth0 connection does not allow me to edit it....I can edit eth1 though...don't know why..as far as I can remember, a few months back I could edit the eth0 connection too...now it does not have the edit option....

---

### Post by Iowan on 2009-12-25
> **krishnamohan said:**
> 
How do I arrange it so that eth1 is connected as the computer starts up?To have the connection at boot (as opposed to login), you could move the definition to */etc/network/interfaces*. However, this will make NM ignore it - and you may end up with both interfaces active.

---

### Post by krishnamohan on 2009-12-26
Oh no...I don't want that...then just want eth1 to go online at login.....

---

