---
title: "Help! my internet won't work after installation with wubi?"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by yummybear on 2011-05-23
Hi i installed ubuntu with wubi a couple of times before on the same pc but everytime i have this same problem that i can't seem to find my answer to on any forum anywhere or even on a simple webpage. i am using a desktop pc with a realtek ethernet card (no wireless card) which is connected to the internet through a home network. this works fine in windows but when i boot up in ubuntu it tries to connect (through auto eth0) but never connects, always coming up with the same message ( auto eth0 disconnected). does anyone know what could be causing this? 

Thanks very much!

Yumybear.:confused:

---

### Post by yummybear on 2011-05-23
Not to sound disrespectful to the makers of ubuntu but this is the second time i have posted this message in the pas few days and not once has there been an answer on this i would have loved to have used ubuntu but considering that the support for it is crap. maybe i should just stick to windows...:(

---

### Post by Kirboosy on 2011-05-23
Welcome to the forums Yummybear!

Do you have static IPs setup on your network or do you use DHCP?

---

### Post by yummybear on 2011-05-23
Thanks so much for replying! seriously. i have a static ip address and i'm using a BT home hub router.

---

### Post by Kirboosy on 2011-05-23
Aha I knew it! :) 

Ubuntu by default is set to DHCP so if you didn't change the network settings to static this would be why you aren't getting a internet connection.

1. Open System-->Preferences-->Network Connections

2. Double click on the "Wired" 'auto eth0'

3. Under "IPv4 settings" tab change the Method: from Automatic (DHCP) to Manual

4. Click the "Add" button and enter your network settings. :)

~Caboose

---

### Post by yummybear on 2011-05-23
Ok just a sec and i'll switch back over to ubuntu and i'll let you know how it goes thanks very much for your help caboose!:D

---

### Post by yummybear on 2011-05-23
errmmmm. it's asking for a device MAC address and some other mac address before it will let me do anything. i'm truely not sure what to do here. lol

---

### Post by Kirboosy on 2011-05-23
Oh. You are talking about under the "Wired" tab. I would just leave it blank. On my system both boxes are blank (I believe blank just lets you use the real MAC address.) You can skip to the IPv4 Settings tab :)

---

### Post by yummybear on 2011-05-23
oh ok thanks. ok i'll try again cause i think i may have gotten a little confused and done something wrong.

---

### Post by Kirboosy on 2011-05-23
Did you figure it out?

---

### Post by yummybear on 2011-05-23
nope i'm still having trouble... just give me another wee while...lol i'll get it eventually i know i will! lol

if i still need help( which i'm sure i will) i'll be sure to let you know!

Thanks very much.

---

### Post by yummybear on 2011-05-24
ok i'm still having trouble with this when i go into the IPv4 tab and click add it asks me for an address which i'll assume that's my ip address. the a 'netmask'. now all i can think this is is my subnet mask because i can't find a number for "net mask" and then it asks for  a gateway which again i'll assume is my default gateway. i have entered all of this. it says it has connected to the internet and the when i try to access it through firefox or even by trying to download from ubuntu software centre thing. it acts like i'm not connected at all...

i honestly don't know what i'm doing wrong....this is sooo frustrating!
:mad:

---

### Post by yummybear on 2011-05-24
hellooo! ok surely someone other than caboose who i talked to about this yesterday must know something about this problem!

---

### Post by Kirboosy on 2011-05-24
Ok, Netmask (defaults anyways) should be 255.255.255.0

Why can't you change your router to DHCP?

Also you might want to write down your IP settings from Windows that way its the same in Ubuntu.

---

### Post by yummybear on 2011-05-28
Hi again caboose! ok first off thanks very much for your response on my question to the net mask thing. As for changing my router to DHCP i would do it but i have no idea how i could do that otherwise i would. lol!

Thanks again!:)

---

### Post by Kirboosy on 2011-05-28
Ok, I've never worked with BT so I have no idea if this applies to your model or not. This guide has instructions to turn off DHCP so if you just reverse it you should be able to turn it back on. :)

[How do I change the DHCP settings of the BT Home Hub?]("http://btybb.custhelp.com/app/answers/detail/a_id/9011/~/how-do-i-change-the-dhcp-settings-of-the-bt-home-hub%3F")

Hope that helps.

---

