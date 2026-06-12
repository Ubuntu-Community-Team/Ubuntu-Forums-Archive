---
title: "getting Belkin F5D7011 to start automatically"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by towy71 on 2006-06-02
I bought Belkin F5D7011 on impulse having plugged it into Latitude CPi running Ubuntu Dapper flight7 and the card was recognised but not functional.
Installed Dapper.rc and then used help from [here]("https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver") which got the card working, hurrah but have to run ```
sudo iwconfig eth0 ap any
```to get it working, the same command works after reboot.

Can someone please help me to get it to work automatically?](*,)

---

### Post by roels on 2006-06-02
Have you tried adding something like this to /etc/network/interfaces:
```
iface eth0 inet dhcp
wireless-ap any
auto eth0

```

---

### Post by towy71 on 2006-06-02
my /etc/network/interfaces is already:
```
auto eth0
iface eth0 inet dhcp
wireless-essid any
```
but I still have to type
```
sudo iwconfig eth0 ap any
```
I was just hoping to get it to do that last bit automatically

---

### Post by roels on 2006-06-02
There's a difference between your and my /etc/network/interfaces:
You use:
```
wireless-essid any
```
I suggest you use instead:
```
wireless-ap any
```
Roel.

---

### Post by towy71 on 2006-06-02
nope, that didn't work :confused: ](*,)

---

### Post by roels on 2006-06-02
Maybe your the module for the Belkin card is loaded too slow, so it is not loaded before the network startup script runs during boot up. I have had the same problems with another card.
You can consider adding the following to /etc/init.d/bootmisc.sh
```
iwconfig eth0 ap any
```
This is a quick & dirty method, but it might work.

---

### Post by entangled on 2006-06-02
The idea of putting iwconfig command in bootmisc.sh certainly worked for me. 
My Atheros 5006EXS in a Mac Mini will not connect until I do 'sudo iwconfig ath0 channel 1'. Then it starts scanning frequencies and finally locks on to channel 1 (my AP is using that). 
I put this command in bootmisc.sh and it always works at boot time.

---

### Post by towy71 on 2006-06-02
Thanks for the idea but i'll put that on the backburner for the moment in the hope that there is a more elegant solution ;)

If I were to do as you suggest where would I put the command in that file?

---

### Post by entangled on 2006-06-02
... where would I put the command in that file?
Put it near the end of bootmisc.sh; line before the exit.

---

### Post by towy71 on 2006-06-02
ok thhat worked ;) thanks for that. yay

---

### Post by towy71 on 2006-06-03
belay that, it was  a horrible hack and didn't work when starting up again after suspending but [this post]("http://www.ubuntuforums.org/showthread.php?t=187498")  works  flawlessly :D

---

