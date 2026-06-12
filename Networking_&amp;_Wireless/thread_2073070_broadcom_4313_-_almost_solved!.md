---
title: "broadcom 4313 - almost solved!"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by a z on 2012-10-18
after years of trying to talk my wife into a dual boot on her Dell laptop (Inpsiron N4010) i found out it has the dreaded 4313 chip. i'm gonna look like a schmuck if i can't make this work.

been trollin' this forum for days, to NO avail - tried everything. and now, in my bleary-eyed desperation, i got it to work IF (after a reboot) i open a terminal, and go:
sudo modprobe wl [w/ password]

then

lsmod | grep wl

then the spinny icon spins, and all is well.
so, how can i have it work, without entering this? 
a startup script? 
add a /etc/modules entry?

so close...

---

### Post by ahallubuntu on 2012-10-18
You can try adding the line

wl

to the end of /etc/modules, that might do it.

Another thought: spend $10 on eBay and replace that crappy Broadcom card with an Intel 6200 card (which will also add a 5GHZ radio).  The Intel card should be supported out of the box.

---

### Post by a z on 2012-10-18
i believe i already tried adding wl to /etc/modules - no good.

i like the replace-the-darn-thing idea. is that something a slightly-savvy guy could attempt? (working on laptops scares me, especially my wife's)

---

### Post by ahallubuntu on 2012-10-18
I've upgraded lots of wireless cards in laptops.  Sometimes it's super easy.  You have to access the wireless card itself (often under a panel on the bottom of the laptop; sometimes under the keyboard), remove the two or three antenna wires (clipped on), remove the card with a screw or two (or sometimes just a clip), swap in the new one, and you're done.  To see exactly how to do it for your Dell, look for a service manual on their website.  Should tell you exactly how to remove/replace the wireless card.

Don't try upgrading the wireless card on a Lenovo or HP laptop - they whitelist their cards so you must use an exact approved replacement card.  Otherwise, the laptop won't even POST - you'll get an error message instead until you remove the card.  On a Dell, no problem.

The key is getting a compatible wireless card.  Dell has sold your laptop with the Intel 6200, which is why I recommended it.  Know that Intel makes two different versions of this card: one for HP and Lenovo and one for everyone else.  Just make sure you don't get the HP/Lenovo version of the card and you should be good.  You don't even have to get the "Dell" card.

(In Windows, though, you should download the Intel wireless card driver from Intel before replacing the card, so you can install it afterward easily the next time you boot Windows.)

You can find this card on eBay for about $10 shipped if you live in the US.  Avoid new cards from Asia - I've personally had bad luck with them not being exactly what they were advertised to be.  I prefer a used card that came out of another laptop.

If in doubt, look on Youtube for examples of replacing a laptop wireless card.  You'll probably find getting the antenna wires off is the hardest thing to do.

---

### Post by a z on 2012-10-19
so - in the meantime, does anyone know how i'd write/implement a startup script (lubuntu 12.04) that would work the same as running these 2 commands in a terminal, after a reboot?

sudo modprobe wl

lsmod | grep wl


until i have the $ for a new wifi-card, i'd love to make this work. i can enter these commands, but i don't want to make my already-linux-suspicious wife have to...

thx

---

### Post by chili555 on 2012-10-19
Depending on your exact card, *wl* may be incorrect. Let's dig a bit. Please run and post:```
lspci -nn | grep 0280
lsmod | grep -e wl -e b43 -e ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by scoon on 2012-10-19
> **a z said:**
> so - in the meantime, does anyone know how i'd write/implement a startup script (lubuntu 12.04) that would work the same as running these 2 commands in a terminal, after a reboot?

sudo modprobe wl

lsmod | grep wl


until i have the $ for a new wifi-card, i'd love to make this work. i can enter these commands, but i don't want to make my already-linux-suspicious wife have to...

thx

Hey there, 

/etc/rc.local is meant for this.

Thanks, 

Skip

---

### Post by Datalocust on 2012-10-19
> **scoon said:**
> Hey there, 

/etc/rc.local is meant for this.

Thanks, 

Skip


I had this same problem a for a while and I fixed it.  Here is what I did.

1. Download the library files for the b43 card and put them in a folder in /lib/firmware.

2. Create a new entry in your /etc/modules file with just the line b43.

3. Reboot your computer it should go find and then activate your card on boot.

This eliminates the need for you to have to use the sudo modprobe "FolderName" where the drivers and lib files are located after each boot.

*Side Note* I have the drivers and lib files required and full instructions if you need them just let me know I can send them to you or post them here, doesn't matter..
~ Datalocust

---

### Post by chili555 on 2012-10-19
I strongly suggest we confirm exactly what card a z has and what the best driver is before we go too crazy here. Just for instance, bcmwl-kernel-source, from whence *wl* comes, blacklists *b43*. It will hardly help to simultaneously add *b43* to /etc/modules *AND* blacklist it! Let's wait and see.

---

### Post by a z on 2012-10-19
thanks fellas,
at work now, will try these suggestions at home this afternoon.

and for the record, after a reboot, running those two commands DO make it work (until i reboot again, of course)

almost there,
a z

---

### Post by a z on 2012-10-19
yes chili,
will post output per your earlier suggestion this afternoon (after 4:00 est)
thx again

---

### Post by a z on 2012-10-19
okay.

lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
 
lsmod | grep -e wl -e b43 -e ndis
wl                   2646601  0 
lib80211               14040  2 wl,lib80211_crypt_tkip

if it means anything(and it might not), the "0280" in the first one, and the "wl"s in the second one appeared in red font in lxterminal.

any ideas?

---

### Post by chili555 on 2012-10-19
> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01)Ahhh! The troublesome 4727! Yippee! There are two ways to get this going and *wl* is one of them, obviously. The other is *brcmsmac*. Let's make sure it isn't loading and conflicting:```
lsmod | grep brcmsmac
```If it does appear, we need to blacklist it, but don't take any action if it isn't loaded:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
exit
```Now, let's try to find out why *wl* isn't loading as expected:```
cat /etc/modules
```At the end, it should say:```
wl
```If not, add it:```
sudo su
echo wl >> /etc/modules
exit
```Reboot. Did your wireless start? If not, let's dig deeper:```
dmesg | grep -e wl -e b43 -e ndis
```> if it means anything(and it might not), the "0280" in the first one, and the "wl"s in the second one appeared in red font in lxterminal.It's highlighted in red just to show you the term you grepped (looked)for. Otherwise meaningless.

---

### Post by a z on 2012-10-19
wow, what an ordeal..

did:
lsmod | grep brcmsmac
nothing...

did:

cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lib80211_crypt_tkip

so i added wl to /etc/modules as you suggested. rebooted, but boot froze at the blue, lubuntu boot graphic (couldn't remamber the keys to go non-graphic boot.
finally chose an older kernel from grub screen, booted okay - no wireless.
changed /etc/modules back, and successfully rebooted into latest (12.04) kernel - whew!

so now, i can once again do my 2 commands, and connect. the next output looks like this(again)

dmesg | grep -e wl -e b43 -e ndis
wl                   2646601  0 
lib80211               14040  2 wl,lib80211_crypt_tkip

seriously, until i can get a new wireless card, i think i just want to make a startup to do those 2 commands at boot. it may not be "correct", but at least that works.
oy veh,
a z

---

### Post by a z on 2012-10-19
here's my cheesy pseudo-solution:

just added my 2 little commands to /etc/rc.local 
modprobe wl
lsmod | grep wl

rebooted, and it freakin' worked!
been harping on my wife for years to do a dual boot (w/ win7). now she has a wonderful working wireless Lubuntu dual boot, and i don't look like a schmuck for messing up her laptop! Yay!
thanks to all - yeesh!
a z

ps, will keep my eye out for that intel 6200 in the meantime ;)

---

### Post by chili555 on 2012-10-19
> just added my 2 little commands to /etc/rc.local
modprobe wl
lsmod | grep wl

rebooted, and it freakin' worked!All's well that ends well, I guess. This part is completely meaningless and I suggest you remove it:```
lsmod | grep wl
```Also, I suspect what's wrong with /etc/modules is this:> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

[COLOR="Red"]lib80211_crypt_tkip[/COLOR]
I'd remove it and leave rc.local as is since you know it works.

I'm glad it's working by whatever means.

---

### Post by a z on 2012-10-20
thanks again,
i will look at that, too.

---

### Post by Datalocust on 2012-10-21
A Z has repeatedly said that he has the 4313 Broadcom card and that is exactly what I found is in my system.  I tried everything else and the only way I got it to load on boot was to put the repository of the 4313 files into a single directory and call it to load on boot without requiring sudo access or issuing commands.

Just offering my experience fixing these cards.   

Chili555 - You are correct however if it is a completely different card it might not work.  The only thing I forgot was that you have to make sure to comment it out of the STA Broadcom line in the .blacklist.conf file to have it load on boot.  This will cause 12.04 to not recognize it as a proprietary required driver only for the boot...

~Datalocust

---

