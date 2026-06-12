---
title: "cant connect when security is enabled"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by rastro123 on 2009-09-24
I've got wicd manager installed and when ever I go to cafe's where they have free wifi access, they give me the wep or whatever code it is, but my pc only ever connects when there is no security enabled, like in Macdonalds in france. Once,- I got it connected to a friends wpa connection but at first it would not connect, then I went and sat right next to the box, dont really know what I did, but then it connected all of a sudden. 
What does the order of sequence mean? I dont know what a pre-connection script is, or a post-connection script, or a disconnection script. I dont know if I should be using pre shared key or passphrase or I.p. static. or dns static. Its got me going crazy and also the poor bird working in the cafe. She hadn't a clue either. Please can anyone help with this and tell me what Im doing wrong? Many thanks.

---

### Post by superprash2003 on 2009-09-24
you just need to make sure you select the right authentication key type like 64bit ,128bit etc

---

### Post by rastro123 on 2009-09-24
Thanks for the fast reply, but can you tell me how I do this please? Is it the space directly above where I type the wep key, code in? Having always used wireless connections wherever I can get a connection, I dont have very much knowledge of the hows and whys. Thanks mate

---

### Post by rastro123 on 2009-09-24
Ive just been going round the preferences in wicd and I dont see anything said of 64 bit or 128 bit encryptions. How do I find it pls? - oh, and what if the bird for example in the cafe does not know what it is? How do I find it? Thanks

---

### Post by rastro123 on 2009-09-24
why bother? there is nowhere that lets change/elect the encrytion as you described. Anyone out there have any ideas pls. Im getting so frustrated here!

---

### Post by rastro123 on 2009-09-25
come on folks! Hasnt anyone got any ideas for me pls? - I just came from another place with wpa enabled, and they gave me the key, but the pc still would not connect.Security is cool but to have so much that you cant get past it is so uncool, Im getting propper pissed off about it now, pls someone help me out here!

---

### Post by rastro123 on 2009-09-27
ok, so no one knows. .....Ive been thinking. I little while ago I tried to make a usb wireless adapter work because I wanted to try out other distros that did not support the wirless that this pc has (broadcom 4312) I tried installing many different drivers from ralink, but without sucess. Now could this be whats screwing me now? I just came from another place with security enabled on their wifi, they gave me the code, and still the pc will not connect. Is there a way that I can get rid of any changes I've inavertantly  made and go back to as it was before I started messing? Or would it be better to do a re-install of the system. Can I do a ''repair'' from the cd? Thanks loads if anyone can help.

---

### Post by cariboo on 2009-09-27
Truthfully if you made a lot of changes, without keeping track of what you did, it may be better to reinstall.

You didn't say what version you are using, but try using Network Manager instead of wcid, and make sure you have wpa-supplicant installed. In Juanty it installed when you install wireless-tools.

---

### Post by rastro123 on 2009-09-27
thanks mate, - how do I re-install the network manager instead of wicd, and I assume the wpa supplicant is in the repositories? Im using jaunty, buy the system is in spanish, as Im a brit but introduced to pc's in spain long  time ago.The other day I also wondered about this wicd and took it off, thinking network manager would come back - wrong again, wasn't I so went to another pc and downloaded the package and re-installed it again. I was a bit worried I was going to lose all my half-downloaded things! As long as there is no security its cool.

---

### Post by rastro123 on 2009-09-27
wpa supplicant is there ok, but I dont see anything in the synaptic packets about the network manager. Can you tell me pls if there is a command to re-install it. I suspect thats the way to do it. Many thanks for your advice.

---

### Post by rastro123 on 2009-09-30
hi, Today I did a re-install of jaunty, gone back to network manager. I did all my updates at a free place with no security. I then went to my friends place with encryption and put the code in, and still it won't connect. I don't know much about how networking works, but I said to him how about resetting the wireless modem, but he said not to do this, as his tech man said not to. The modem is called ''orange'' I dont know what brands you have there, but do you have any suggestions for me please. Thanks.

---

### Post by v2rocketboy on 2009-10-01
Sorry to add onto this thread with no help, but I also have the same problem, I'm running ubuntu 9.04, my internet connects fine to an unsecured network but when I go to put encryption on it, whether it be WEP, WPA, or other, and either 128 bit or 68 bit it just does not want to connect and keeps looping, asking for my password. So yeah it is quite frustrating, any solutions?:(

---

