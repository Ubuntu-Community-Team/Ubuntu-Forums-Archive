---
title: "Can't find W.D. My Book World"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by jr3571 on 2009-05-19
I've been using Ubuntu for about half of a year and thanks to the forums I've managed to get everything working except this. I recently bought a western digital my book world hdd and I don't have any clue how to get it recognized on my wired or wireless network. After calling w.d. tech support it shows up on a x.p. machine but not on my Ubuntu 9.04 desktop or laptop. Any help would be appreciated. Thanks, Joe.

---

### Post by cariboo on 2009-05-19
It would make things much easier if you told us how you access the drive, but after much searching, I assume you access it over a network. If you know the ip address of the device, can you ping it? If you aren't sure of the ip address you can use something like this:

```
sudo nmap -PR -sP 192.168.1.0/24
```

to find the ip address. Namp is in the repositories.

Once you find the ip address, you should be able to access the drive in nautilus by typing something like this:

```
smb://192.168.1.200
```

in the location bar. Subustitude your device's ip address for the above.

---

### Post by jr3571 on 2009-05-19
This is what came up with the code you posted when I entered it in terminal.Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-05-19 20:18 EDT
Host 192.168.1.1 appears to be up.
MAC Address: 
Host 192.168.1.100 appears to be up.
MAC Address:                  (Western Digital)
Host 192.168.1.101 appears to be up.
Nmap done: 256 IP addresses (3 hosts up) scanned in 4.47 seconds
joe@joe-desktop:~$  00:90:A9:6D:98:08 
bash:                         : command not found
joe@joe-desktop:~$ smb://192.168.1.200
bash: smb://192.168.1.200: No such file or directory
joe@joe-desktop:~$ 
I'm not sure where to type it into nautilus. Isn't that the file browser? When I type any of the ip's in the go to box I get this error.Error: Failed to retrieve share list from server
Please select another viewer and try again. Thanks for the help.

---

### Post by jr3571 on 2009-05-20
When I booted up my computer this afternoon it updated and I did the steps posted above and it connected to the hdd. I couldn't believe it. Everything is working. Thank you very much.

---

### Post by Juanpablomdq on 2009-06-30
Hi! Im a new Ubuntu User.. Im having the same problem... i just installed ubuntu in my computer and I can see my WD in Places --> network (i guess that would be the traslation i have it in spanish) but i cant see the files in it. (all i can see when i double clic it is the printers icon) I was using it in windows xp but i erase that OS so now i cant access thos files from anywhere... 

The HD is conected to an ethernet adaptor (i have two one for my internet conection and another especially for my wd) 


I tried typing  [COLOR=blue]http\\mybookworld [COLOR=black]on my browser but all that i acomplished was to google search it... 

I tried doing what u said and this is what i got:

juan@juan-desktop:~$ sudo nmap -PR -sP 192.168.1.0/24

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-06-30 01:01 ART
Nmap done: 256 IP addresses (0 hosts up) scanned in 0.10 seconds


any idea of what i should do? or what im doing wrong? 

thanks a lot!

Juan Pablo





[/COLOR][/COLOR]

---

### Post by dmizer on 2009-06-30
Juanpablomdq, please refer to the 6th link in my sig :)

---

### Post by Juanpablomdq on 2009-07-01
Hi!! Thanks for your quick response! I tried doing a couple of the things u said but without success...

I have done some progress though... First of all i tried looking for the Mybook ip 

sudo iftop -i eth0 (thats the ethernet adaptor to which is plugged)

Then i set my ip adress to one number above ( 169.254.21.xx+1)  and it worked for a little time.

What im trying to do know is to set a fix ip (i dont know the word --> when the ip is set to one number) but when i try to access my WD the user and password is not working. I tried reseting it and wrote user: admin password: admin but still i cant get in...  Whats going on?? I tried this several times but the user and password dont seem to work...

Any sugestions? 

this is my hd (in the WD page is the new model)

[http://images.google.com.ar/imgres?imgurl=http://www.gadgetastic.co.uk/wp-content/uploads/2009/02/world-book-western-digital-white.jpg&imgrefurl=http://www.gadgetastic.co.uk/1tb-western-digital-external-network-hard-drive/&usg=__xVlR2sP5k_ZGR8neIo6kyRqYLwA=&h=500&w=324&sz=9&hl=es&start=49&um=1&tbnid=moskIfsqCB9MnM:&tbnh=130&tbnw=84&prev=/images%3Fq%3Dwestern%2Bdigital%2Bmy%2Bworld%2Bedition%2B1tb%26ndsp%3D20%26hl%3Des%26sa%3DN%26start%3D40%26um%3D1](http://images.google.com.ar/imgres?imgurl=http://www.gadgetastic.co.uk/wp-content/uploads/2009/02/world-book-western-digital-white.jpg&imgrefurl=http://www.gadgetastic.co.uk/1tb-western-digital-external-network-hard-drive/&usg=__xVlR2sP5k_ZGR8neIo6kyRqYLwA=&h=500&w=324&sz=9&hl=es&start=49&um=1&tbnid=moskIfsqCB9MnM:&tbnh=130&tbnw=84&prev=/images%3Fq%3Dwestern%2Bdigital%2Bmy%2Bworld%2Bedition%2B1tb%26ndsp%3D20%26hl%3Des%26sa%3DN%26start%3D40%26um%3D1)



thanks again!!

---

### Post by dmizer on 2009-07-01
Try this: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

If you are still unsuccessful, have a look at the 2nd link in my sig.

P.S.
You'll be better off with DHCP rather than static (fixed) IP. As long as you followed the fix for problem three in the Windows share browsing fixes, you should be OK with DHCP.

---

### Post by TIMCALLONLINE on 2009-10-04
I bought a My Book World recently and initially managed to access it from my Ubuntu machine. However, now, when I try to access it from 'Network' it says 'Failed to retrieve share list from server'.

I am able to access it from our Mac and, usually from our Vista machine.

Any suggestions?

---

### Post by dmizer on 2009-10-04
> **TIMCALLONLINE said:**
> I bought a My Book World recently and initially managed to access it from my Ubuntu machine. However, now, when I try to access it from 'Network' it says 'Failed to retrieve share list from server'.

I am able to access it from our Mac and, usually from our Vista machine.

Any suggestions?

See the 6th link in my sig. If that doesn't work, refer to my post directly above yours.

---

