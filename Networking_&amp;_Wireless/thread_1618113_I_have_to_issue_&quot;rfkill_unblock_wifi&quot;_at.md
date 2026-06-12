---
title: "I have to issue &quot;rfkill unblock wifi&quot; at every boot..."
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by Quaxo76 on 2010-11-10
After installing 10.10 on my laptop (where everything was OK witn 10.04) the wifi stopped working. I can get it to work with the command
```
sudo rfkill unblock wifi
```
but after every reboot I have to re-issue that command again (actually that's not entirely true, sometimes it seems to "stick" through a reboot).
Is there a way to tell rfkill to never block wifi, without having to tell it so explicitly every time?

Thanks,
Cristian

---

### Post by uncaspi on 2010-11-10
There is a workaround. You could put the command in /etc/rc.local

---

### Post by syed.rakib.al.hasan on 2011-04-30
> **uncaspi said:**
> There is a workaround. You could put the command in /etc/rc.local

can u specify the exact sentence to include in rc.local file???
before or after 'exit 0'????
semi-colon or no semi-colon?????

help this newbie please :)

---

### Post by chili555 on 2011-04-30
Please do:```
sudo gedit /etc/rc.local
```Right *above* Exit 0 please add:```
rfkill unblock wifi
```Proofread, save and close gedit. Enjoy!

---

### Post by syed.rakib.al.hasan on 2011-05-04
> **chili555 said:**
> Please do:```
sudo gedit /etc/rc.local
```Right *above* Exit 0 please add:```
rfkill unblock wifi
```Proofread, save and close gedit. Enjoy!

i have done that......... still i need to issue "*rfkill unblock wifi*" at **SOME** boot times........ not at **ALL** boot times.

this is a workaround...... how possibly can we solve this????

---

### Post by NateFalken on 2011-12-01
I enter the following:

rfkill unblock all

But the next line always appears as that base start line that you would just get from hitting enter.

" rfkil list " brings the following:

0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

if you could help me that would be great!!! :D
I'm also running Ubuntu 11.10

---

### Post by jedi-penguin on 2012-02-27
Make sure that the wifi card isn't disabled by the keyboard. My dell laptop is fn+f2 to diable and enable wifi card.

---

