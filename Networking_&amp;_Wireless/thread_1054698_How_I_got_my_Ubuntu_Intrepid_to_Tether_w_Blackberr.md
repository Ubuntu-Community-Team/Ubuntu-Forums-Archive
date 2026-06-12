---
title: "How I got my Ubuntu Intrepid to Tether w/ Blackberry"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by snwagner on 2009-01-29
Well...
I spent a lot of time fussing over this, several sleepless nights attempting to find a way to tether w/ my blackberry.

I went everywhere searching, attempting to install xmblackberry, attempting to install openmotif... I did everything!  

Now, I'm just a newbie, but this is how I did it...

I downloaded barry (hopefully attached) from [http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564](http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564)

Once I had barry installed, I then followed the instructions here: [http://www.netdirect.ca/software/packages/barry/modem.php](http://www.netdirect.ca/software/packages/barry/modem.php)

But... there is no PPD script for alltel...
So I 
sudo gedit /etc/ppp/peers/barry-sprint
In the terminal

(note: only the sprint 1 to my knowledge will work)

In that new window, I looked for the username, there I put
[email]yourphonenumberhere@bb.alltel.net[/email]

under that is a place for a password...

put in alltel

Now save that file

now in terminal write
sudo gedit /etc/network/interfaces

go to an empty line and put in 

iface ppp0 inet ppp
	provider barry-sprint

save that file.

Now in terminal type 
sudo ifup ppp0

You should see

ppp0: ERROR while getting interface flags: No such device
Serial connection established.
using channel 3
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MD5> <magic 0xf33b1ee9> <pcomp> <accomp>]
sent [LCP ConfRej id=0x1 <magic 0xf33b1ee9> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0>]
rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <auth chap MD5>]
sent [LCP ConfAck id=0x2 <asyncmap 0x0> <auth chap MD5>]
rcvd [CHAP Challenge id=0x1 <ce6e2fe42e583f6a427b37d4b15d2eb9b096883dc32d>, name = ""]
sent [CHAP Response id=0x1 <380a0eeb1e9acfcd969df76e93268362>, name = "5127555784@bb.alltel.net"]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr 209.97.109.74>]
sent [IPCP ConfAck id=0x1 <addr 209.97.109.74>]
rcvd [IPCP ConfNak id=0x1 <addr 96.15.55.244> <ms-dns1 166.102.165.11> <ms-dns2 166.102.165.13>]
sent [IPCP ConfReq id=0x2 <addr 96.15.55.244> <ms-dns1 166.102.165.11> <ms-dns2 166.102.165.13>]
rcvd [IPCP ConfAck id=0x2 <addr 96.15.55.244> <ms-dns1 166.102.165.11> <ms-dns2 166.102.165.13>]
Cannot determine ethernet address for proxy ARP
local  IP address 96.15.55.244
remote IP address 209.97.109.74
primary   DNS address 166.102.165.11
secondary DNS address 166.102.165.13
Script /etc/ppp/ip-up started (pid 7067)
Script /etc/ppp/ip-up finished (pid 7067), status = 0x0

You're online!  You'll need to leave that terminal window open to stay online.  If you want to disconnect, close the terminal window and open a new one (or press ctrl+c in the current window) and type in sudo ifdown ppp0

As long as you're online this way you'll have to leave the terminal window open, but hey... a small price to pay for a great service.

I'm getting 1.1 mbps according to speedtest.net.

Again, this is for alltel only, but feel free to experiment!

I know this works because I'm on it right now.

---

### Post by acmebot on 2009-02-21
I did the same, downloaded, installed and compiled all that stuff. Then found the binary packages for barry here:
[https://launchpad.net/~doctormo/+archive/ppa]("https://launchpad.net/~doctormo/+archive/ppa")
I added 
```
deb http://ppa.launchpad.net/doctormo/ppa/ubuntu intrepid main
```

```
sudo apt-get install libboost-serialization1.34.1
sudo apt-get install libbarry0
sudo apt-get install barry-util

```

then the instructions here:
[http://www.netdirect.ca/software/packages/barry/modem.php]("http://www.netdirect.ca/software/packages/barry/modem.php")

then all I had to do was run:
```
pppd call barry-rogers
```

It worked!

to disconnect:
```
poff
killall -9 pppob
```

I hope this saves someone else an afternoon...

---

