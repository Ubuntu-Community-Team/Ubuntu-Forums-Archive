---
title: "Found my problem with internet... (for newbs)"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by sethfc on 2006-07-03
so i'm starting a thread for newbies with the same problem as mine.

in terminal, i use the command "lspci"

i notice that my wired ethernet controller is a Realtek Semiconductor Co ...... 8139 C+ (Rev 10)

apparently there are problems with this controller.  unforunately for me, this is a laptop.  BUT, i do have a wireless controller (Atheros Communications) and i have no wireless network at home.... so i gotta fix the realtek.

so, i'm going to start searching and trying things.  this is what i've tired so far:
1. disabling IPv6
2. blacklisting tulip
3. dmfe

no avail so far.... more news to come

---

### Post by FenrisAbraxas on 2006-07-03
can you post the output of:

```
sudo lsmod
```

Please?

I used to had a network card based on the same chipset, so probably i can help you.

---

### Post by sethfc on 2006-07-03
thats a long *** list =p
i'm currently on my windows desktop (seeing as i cannot get the laptop on the net)

is there something specific from lsmod you want to see?  i could type it all out if i HAVE to... lol

---

### Post by sethfc on 2006-07-03
been workin hard....

i changed the driver from 8139cp to 8139too - still no success
at one point i could ping my router fine, but using GOOGLE'S ip address, i still couldnt get a webpage
i did some more B.S., now i cant even ping my router... lol

damn :(

---

### Post by sethfc on 2006-07-03
i booted up knoppix on a CD... bad news

even firefox on knoppix wont work...

i'm gonna give it a rest for a lil

EDIT: this is a Sony Vaio PCG-K25 laptop...

---

### Post by FenrisAbraxas on 2006-07-03
Probably this will sound a little stupid but, does the card works ok? :P

It's kinda weird. Also im want to see if your realteck module is properly loaded and it's just configuration issues or if it's the module itself :S

I'm at work and have to use Winblows but as soon i get home i'll look for the module name :(

---

### Post by sethfc on 2006-07-03
yea the card works... pinged the router ;)

---

### Post by FenrisAbraxas on 2006-07-04
Hmmm with the driver and config when you can ping your router did you tried a:
```
sudo ifup eth0
```

or whatever device is your ethernet interface? :S

You can also try to see what the problem is using:

```
sudo ifconfig
```

---

### Post by sethfc on 2006-07-04
ok i got everything working, BUT only with IP addresses.

so...whats the resolv.conf file for ubuntu?  i need to fix that...

---

### Post by sethfc on 2006-07-05
bump...

---

### Post by woedend on 2006-07-06
hi seth, perhaps post how you fixed it for others?
Anyhow, /etc/resolv.conf you can use OR if you go to sys-admin-networking you can add the dns servers there.
for starters you can try
4.2.2.1 and 4.2.2.2
they used to work, but slowly.  You can find out the correct dns from your ISP.

if you use resolv.conf, precede each server with the word nameserver.  For example here is my resolv.conf

nameserver 74.128.1.31
nameserver 74.128.1.33

---

### Post by sethfc on 2006-07-06
yea dont worry i have had it all down for a while....

[img]http://www.sethfc.us/Screenshot.jpg[/img]

basically, this is all you have to do:

sudo ifconfig eth0 192.168.1.123
sudo route add default gw 192.168.1.1

then go into your resolv.conf and enter your DNS address (SO, if you have a windows box on your home network, goto the Command Prompt and type ipconfig /all - and it will list your DNS server IP)  once you have that DNS Server IP, just type "nameserver theIP" - hit save.

bam.  FYI i've never used linux in my life, except i installed it once when i was 14 (3 years ago) and i thought to myself ... "oh shit."

cheers

P.S. - you have to do steps 1 and 2 (so the sudo commands) everytime you bootup - SO i'd recommend putting those commands in a gedit document, so you can quickly copy and paste into the terminal on bootup.  ALSO, your IP addresses on the sudo commands may vary depending on your stuff.  but it's safe to say (since i have a basic as hell setup here at home) that those #s should work for you.  if not, just check your windows box by using that ipconfig /all command.

---

### Post by takakia on 2006-07-06
[QUOTE=sethfc]

sudo ifconfig eth0 192.168.1.123
sudo route add default gw 192.168.1.1

[/QUOTE]

is that your fixed ip address ?? I have a Dynamic IP, any idea how to make it work.   

> (since i have a basic as hell setup here at home) that those #s should work for you.  if not, just check your windows box by using that ipconfig /all command.

I have exactly the same problem and I can only visit sites if I know the IP addresses of those sites.  I m also having a realtek 8139 chipset lan card.

---

### Post by sethfc on 2006-07-06
ok, then you need to edit your resolv.conf

can you do that?

the command you're going to want is...

sudo nano /etc/resolv.conf

to save, hit Cntrl + X
then do as it asks... i think you type "Y" and hit ENTER.

anyway, what you put in there is "nameserver theDNSIP"

do you know how to get your DNS Ip?

---

