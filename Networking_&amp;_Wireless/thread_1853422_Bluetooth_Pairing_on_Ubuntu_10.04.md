---
title: "Bluetooth Pairing on Ubuntu 10.04"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by AnujaM on 2011-10-02
HI,

I'm using Ubuntu 10.04 which has Bluez 4.60.
I'm trying to pair my mobile phone with PC via bluetooth.
I followed these steps :
'anuja@ubuntu:~$ hcitool dev 
 anuja@ubuntu:~$ hcitool scan'

Now for pairing, I found 'Bluetooth-agent' at '/usr/bin/bluetooth-agent'.

'anuja@ubuntu:~$ bluetooth-agent 1234 
 Can't register agent Agent already exists'

bluetooth-agent details are :
'Bluetooth agent ver 4.60 Usage: agent [--adapter adapter-path] [--path agent-path] <passkey> [<device>]'

This might be useful in storing default pass-key.
How to use this bluetooth-agent for pairing??or is there any other way for pairing without using GUI??

---

### Post by jagajugue on 2011-11-10
Same problem here. I tried:

#bluetooth-agent --adapter hci0 1234
Can't register agent
Already Exists

Where are the passes stored?

---

### Post by AnujaM on 2011-12-08
hey...this command works :
hcitool cc connect <device MAC addr>

dis will ask you for pin code on both mobile and pc !!! 
but this commands needs user interface means screen to display pin code but i m using arm development board instead of pc which doesn't have any GUI...so I'm still stuck at this problem !!!

---

