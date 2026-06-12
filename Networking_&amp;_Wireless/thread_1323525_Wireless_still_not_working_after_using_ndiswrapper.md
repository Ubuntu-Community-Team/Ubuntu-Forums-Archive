---
title: "Wireless still not working after using ndiswrapper"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by RRC770 on 2009-11-11
Hey Everyone.
I'm trying to get the wireless to work on an Hp Pavilion dv5000 with a Broadcom BCM4318 wireless LAN. I tried to get it working with the ndiswrapper tutorial found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). Everything seemed fine once I finished with it and I could even find my wireless router and connect to it until I restarted and almost everything disappeared. It still tells me the drivers are installed but it seems they are not being used. ifconfig gives me this (if it's helpful): 

wlan0       Link encap:Ethernet     HWaddr  00:14:a5:a1:b9:bc
                                              UP BROADCAST MULTICAST    MTU:1500   Metric:1
                                               RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                                               TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                                               collisions:0 txqueuelen:1000
                                               RX bytes:0 (0.0 B)     TX bytes:0 (0.0 B)
                                               Interupt:21 Memory:c020400-c0206000


EDIT: I have done a clean install everytime I have tried a new way to fix the issue so it's a count of 4 now. I cannot detect any wireless connections on the computer but I have it Wired right now just in case.

---

### Post by raygj on 2009-11-11
see if this post helps you
[http://ubuntuforums.org/showpost.php?p=8295253&postcount=6]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")
after setting your wireless domain zone to your country code, 
try using the original non ndiswrapper driver .

---

### Post by RRC770 on 2009-11-12
I started to try this but when I got to the end of
 >  	 	 		 			 				#!/bin/bash
##iw reg set <your-country-code>
iw reg set AU 			 		
it gave me 

> command failed: Operation not permitted (-1)

is that bad?

---

### Post by RRC770 on 2009-11-12
SOLVED:  I used this to solve my problem works even after reboot.

> Please follow this procedure instead:
 Step 1: Open Terminal from "Applications->Accessories->
Terminal"
 Step 2: Run the following command (copy-paste each line below to the Terminal then hit <enter> after each line)
 sudo gedit /etc/apt/sources.list
 # Add the following 2 lines at the end of the sources.list file and save the file:
 deb     [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) hardy-cafuego broadcom
deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) hardy-cafuego broadcom
 Step 3: Open Terminal from "Applications->Accessories->
Terminal"
 Step 4: Run the following commands (copy-paste each line below to the Terminal then hit <enter> after each line)
 sudo aptitude update
sudo aptitude install b43-firmware  b43-fwcutter
 Step 5: Reboot and retest your wireless
 You can check out the following threads for more info:
 [http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318](http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318)
[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)


---

### Post by raygj on 2009-11-12
> **RRC770 said:**
> I started to try this but when I got to the end of
 
it gave me 



is that bad?
**do not** enter>  #!/bin/bash
##iw reg set <your-country-code>
iw reg set AU  in a terminal.this **was to set my own country code**.i pasted this inside a new bash text file.
ie.
right click on your desktop--> select Create Document--> select(click on) Shell script
rename to 'setwirelesscountrycode.sh'
double click on 'setwirelesscountrycode.sh' desktop icon
select display button.
a text editor opens up.
replace file' original contents
> #!/bin/bash
with
> #!/bin/bash
##iw reg set <your-country-code>
iw reg set <insert-your-country-code-here>


save & close text editer
put it in the /etc/init.d/ directory.as per previous post instructions
in a terminal enter
 > sudo cp ~/Desktop/setwirelesscountrycode.sh /etc/init.d/ 
note i have updated my [linked post]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")
so please reload it [http://ubuntuforums.org/showpost.php?p=8295253&postcount=6]("http://ubuntuforums.org/showpost.php?p=8295253&postcount=6")

---

