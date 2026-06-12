---
title: "Dell Inspiron 9400 + intel pro 3945abg + dapper live"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by Brachabre on 2006-07-03
argggh I cannot get connected to the internet for the life of me. Dapper acknowledges my wireless! 

First off, lemme ask this --- I use wep-open as my network encryption along w/ an ASCII key


To setup a wep-open along w/ ASCII key   should look like which one of these 2 lines?

sudo iwconfig eth0 key open s:xxxxxxxxxx    (x's equal my numbers)

**_or_**

sudo iwconfig eth0 key restricted s:xxxxxxxxxx


I don't know what else to do. My info is all here. Iwconfig automagically picks up the gateway AP address, the channel and frequency, Managed mode, etc. etc.

Why am I still not getting an IP?

My wireless works perfectally fine on windows xp on the same laptop. Nothing should be hindering my gateway/router from assiging me an ip.

The one thing that always happens (after checking my system logs) is that DHCP always mentions retrieving than some # at the end (in a successive list over and over) 

Dapper also mentions like it's trying to use IPV6 over IPV4 tunneling

Says I don't have IPV4 or something odd.  I don't even use IPV6. I know this is vague but what else should I do? I never can get my wireless working. -- ndiswrapper (installs fine, hardware present, driver present but gives me the same results in the end)   it must be something w/ the configuration

Sigh....I just don't know what else to do. 



Everything looks clear on this screenshot i took for my wireless config settings

---

### Post by awaldram on 2006-07-03
you mention using iwconfig

not sure why you'd do that against an integrated gui,

native gnome
gnome network manager
or my favourite at present cause it actualy works wifif-radar.

but if you are going to use iwconfig then after ascociating which from your screen shot was successfull (see the ap details)  then you'd need to run 'dhclient' to pick up an ip address.

check 'ifconfig' to see your assigned ip address.

---

### Post by awaldram on 2006-07-03
you also mught like to change your encryption key as you've now told the whole  
world ;-)

---

### Post by Brachabre on 2006-07-03
oh don't worry i doctored and messed all the info up in the .txt file befoer posting this. I'm a security freak, I know better than that! :-P

---

### Post by Brachabre on 2006-07-03
UPDATE: I'm not going to install ubuntu on my laptop afterall. I hear problems w/ ACPI and issues w/ overheating -- This scares me!!! I don't want to be threatened by this issue -- waaaay too big a deal for me to want to use Ubuntu on here atm :(

thanks for the time to help me try and get the wireless working anyways!


____________________________======[SIZE=5]THREAD CLOSED[/SIZE]======__________________________

---

