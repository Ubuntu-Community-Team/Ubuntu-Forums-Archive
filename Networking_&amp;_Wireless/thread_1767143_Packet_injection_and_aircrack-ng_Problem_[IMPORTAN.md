---
title: "Packet injection and aircrack-ng Problem [IMPORTANT]"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by unknown01 on 2011-05-25
Hey everybody:
actually I'm new in Ubuntu and i have some problems:
I searched all over the INTERNET and there was nothing to help me with this problem just i get more confused.
My problem is Packet Injection and aircrack-ng
i have an Atheros ar9285 wireless chipset i  don't know how to inject packets and my another problem is that when i type aircrack-ng in Terminal it says that it's not installed so i go to the [http://aircrack-ng.org/](http://aircrack-ng.org/) and download the source when i opened it, i was confused what should i do now!!!
i had found some tutorials but they start after the packet injection.
please someone help me.
Thanks in Advanced.
Ubuntu is very good but it's a little bit hard:P.

---

### Post by fractalman on 2011-05-25
you should be able to find aircrack-ng in the synaptic package manager or the software centre

system>administration>synaptic package manager

Applications>software centre

then start typing aircarack-ng in the searchbox and it should find it, then mark for installation and click apply,

You'll probably want kismet as well, same procedure,

or you could try

```
sudo apt-get install aircrack-ng
```you can compile it yourself from here

[http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide)

packet injection will be dependant on the wireless card so you might have to patch the drivers to get injection to work, I just had to patch my zd1211rw drivers

to test injection 

```
 aireplay-ng -9 wlan0
```

 i would also suggest installing macchanger

```

sudo apt-get macchanger

```

[http://www.aircrack-ng.org/doku.php?id=injection_test&]("http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=0b0b995bccd2b0e098a9247424a17a04")
[DokuWiki=0b0b995bccd2b0e098a9247424a17a04]("http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=0b0b995bccd2b0e098a9247424a17a04")



Should just add that you're better off using tools like aircrack and kismet in a proper backtrack installation, they use a different kernel and can end up breaking your ubuntu install,

[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

---

### Post by fractalman on 2011-05-25
This might help you too

[http://www.aircrack-ng.org/doku.php?id=tutorial](http://www.aircrack-ng.org/doku.php?id=tutorial)

[http://forum.aircrack-ng.org/index.php](http://forum.aircrack-ng.org/index.php)


Good luck :)

---

### Post by unknown01 on 2011-05-25
> **fractalman said:**
> you should be able to find aircrack-ng in the synaptic package manager or the software centre

system>administration>synaptic package manager

Applications>software centre

then start typing aircarack-ng in the searchbox and it should find it, then mark for installation and click apply,

You'll probably want kismet as well, same procedure,

or you could try

```
sudo apt-get install aircrack-ng
```you can compile it yourself from here

[http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide)

packet injection will be dependant on the wireless card so you might have to patch the drivers to get injection to work, I just had to patch my zd1211rw drivers

to test injection 

```
 aireplay-ng -9 wlan0
``` i would also suggest installing macchanger

```

sudo apt-get macchanger

```[http://www.aircrack-ng.org/doku.php?id=injection_test&]("http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=0b0b995bccd2b0e098a9247424a17a04")
[DokuWiki=0b0b995bccd2b0e098a9247424a17a04]("http://www.aircrack-ng.org/doku.php?id=injection_test&DokuWiki=0b0b995bccd2b0e098a9247424a17a04")



Should just add that you're better off using tools like aircrack and kismet in a proper backtrack installation, they use a different kernel and can end up breaking your ubuntu install,

[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

Thank 'fractalman' but when i type in terminal
```
sudo apt-get install aircrack-ng
```it comes:
""Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack-ng""
What should i do now??
and unable to load comes for MACCHANGER too.

And I'm the administrator

Thanks

---

### Post by fractalman on 2011-05-25
You might need to change the settings in the synaptic package manager,  if you open the spm and look under settings for 'repositories, make sure that on the ubuntu software and other sources tabs the boxes are checked , then try those commands again.

---

### Post by unknown01 on 2011-05-25
> **fractalman said:**
> You might need to change the settings in the synaptic package manager,  if you open the spm and look under settings for 'repositories, make sure that on the ubuntu software and other sources tabs the boxes are checked , then try those commands again.
hey men you're the best i tried and checked all and it found aircrack, kismet and macchanger
thanks for the help
now, can you help me with the packet injection, my wireless card is Atheros AR9285.
THANKS IN ADVANCED.

---

### Post by fractalman on 2011-05-25
which version of ubuntu are you running?  i think you need the ath9k driver or the madwifi driver

[http://aircrack-ng.org/doku.php?id=compatibility_drivers](http://aircrack-ng.org/doku.php?id=compatibility_drivers)

[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

[http://aircrack-ng.org/doku.php?id=patching](http://aircrack-ng.org/doku.php?id=patching)


to test your packet injection just open a terminal and type


sudo aireplay-ng -9 wlan0

---

### Post by unknown01 on 2011-05-26
Hey fractalman:
I had read this tutorials before but These are very confusing.
My ubuntu version is 11.04 (Natty Narwhal)
First of all I have a big question:
when i want to use packet injection should i download a file or do something elese?
If i have to download a file, how should i install it?
Please say the details and all of the basics.
Thank you.

---

### Post by fractalman on 2011-05-26
Ok well the first thing you have to do is determine if injection is working or not

open a terminal and type

```
sudo iwconfig
```
this will tell you the interface your using, mines is called 'wlan0' but depending on the drivers you use you might get wif0 or ath0,  whatever your interface is called is what you should use for all commands

Then you need to put your interface in monitor mode,  my monitor interface is called mon0  but yours might be different

```
 sudo airmon-ng start wlan0 
```run sudo iwconfig again and check that monitor mode is enabled

then run the injection test

```
 sudo aireplay-ng -9 wlan0 
```if injection is working you get a message like this

 16:29:41  wlan0 channel: 9  16:29:41  Trying broadcast probe requests...  
16:29:41 Injection is working!  
16:29:42  Found 5 APs    16:29:42  Trying directed probe requests... 
 16:29:42  00:09:5B:5C:CD:2A - channel: 11 - 'NETGEAR'  
16:29:48  0/30: 0%  16:29:48  00:14:BF:A8:65:AC - channel: 9 - 'title' 
 16:29:54  0/30: 0%  16:29:54  00:14:6C:7E:40:80 - channel: 9 - 'teddy' 
 16:29:55  Ping (min/avg/max): 2.763ms/4.190ms/8.159ms  16:29:55  27/30: 90% 
 16:29:55  00:C0:49:E2:C4:39 - channel: 11 - 'mossy'  
16:30:01  0/30: 0%  
16:30:01  00:0F:66:C3:14:4E - channel: 9 - 'tupper'
 16:30:07  0/30: 0%

[LIST]
[*] **16:29:41  wlan0 channel: 9**: This tells you which interface was used and the channel it was running on.
[*] **16:29:41  Injection is working!**: This confirms your card can inject.
[*] **16:29:42  Found 5 APs**: These access points (APs) were found either through the broadcast probes or received beacons.
[*] **16:29:42  00:09:5B:5C:CD:2A - channel: 11 - 'NETGEAR'**: Notice that this AP is on channel 11 and not on our card channel of 9. It is common for adjacent channels to spill over.
[*] **16:29:55  Ping (min/avg/max): 2.763ms/4.190ms/8.159ms**: It an AP responds with one or more packets then the ping times are calculated.
[*] **16:29:55  27/30: 90%**  for teddy: This is the only AP that the card can successfully  communicate with.  This is another verification that your card can  inject. You will also notice that all the other APs have 0%.
[/LIST]

If injection testing doesnt work using the interface wlan0(or whatever yours is called) then try running it on mon0(or whatever your monitor interface is called)


 if you get a different message post the output and then we can work out if its the driver needs patching or not


I'm running 11:04 natty narwahl too but aircrack and kismet use a modified kernel and will most likely muck up your 11:04 install, i'm having trouble with mine at the mo, when i try and use aircrack or kismet my pc just crashes.  i would recommend installing backtrack 5 alongside 11:04 and using that to run aircrack and kismet, it's what backtrack was designed for and i have no problems running aircrack and kismet from backtrack, just a bit of a chore rebooting the pc everytime:)

---

### Post by unknown01 on 2011-05-26
Oh [fractalman]("http://ubuntuforums.org/member.php?u=1295493") I think you don't knew that you are the best but know i tell you that you're the best :D
Thanks meeeen.
first i checked with:
```
 sudo aireplay-ng -9 wlan0 
```and it didn't work then like you said i checked with:
```
 sudo aireplay-ng -9 mon0 
```then it comes:
Trying broadcast probe req.....
INJECTION IS WORKING!
Found 4 APs
and 
.
.
.
.
Thank you men you're the best.
Have a nice day.
but if I had another problems I'll let you know:D

---

### Post by fractalman on 2011-05-26
You're welcome, glad you got it sorted, :)

---

