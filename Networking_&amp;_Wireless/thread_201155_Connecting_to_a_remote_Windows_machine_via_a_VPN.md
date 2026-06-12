---
title: "Connecting to a remote Windows machine via a VPN"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by megalomaniac on 2006-06-21
I'm still a bit new to this Linux thing so you'll have to bear with me:

I've been using Ubuntu for a few months now on and off and think it's great. There is however one thing I can't get working which is preventing me from completely dumping M$ Windows and that's logging into a remote Windows machine via a VPN (which I have zero control over the setup of).

In XP it was easy and required very little information about the network you're connecting to. Just setup the VPN, fire up Windows remote desktop connection and log in, job done. However It's not that simple (at least not for me :( ) in Ubuntu, after many hours of scouring the forums and playing around with config files I've managed to connect to the VPN successfully (or at least I think think I have as it doesn't give any error messages) using PPTP Linux. But that's as far as I've managed to progress, it just connects nothing more.

Which brings me to my questions: What now? I've tried the remote desktop thingy in dapper and I can't get that to work, it just disappears and only comes back with an error if I close the VPN connection. I guess I should ask if it's actually possible to connect to a windows machine in this manner or have I got the wrong end of the stick about what the remote desktop application does? If it is possible is there an intermediate step I'm missing? If so then what information about the internals of the remote network will I need (I currently have the external IP I connect via and the internal IP of the machine I need to connect to, that's all I have and all they'll give me, unless I can give specifics about what I need and why. They only provide the info needed to connect from XP ](*,) )?

Any help / pointers would be much appreciated.

Thanks

---

### Post by cprise on 2006-06-22
Hi. I'm here trying out ubuntu as well.


Xandros Linux will setup a VPN connection to a Windows network automatically. ExtremeTech discusses it here:

[http://www.extremetech.com/article2/0,1697,1738521,00.asp](http://www.extremetech.com/article2/0,1697,1738521,00.asp)


The Xandros editions that support this feature are SurfSide, Deluxe and Business. TigerDirect has SurfSide at $29 after rebate (pretty decent since you get a USB headset setup for Skype in the box).

[http://www.tigerdirect.com/applications/SearchTools/search.asp?keywords=xandros&image1.x=0&image1.y=0](http://www.tigerdirect.com/applications/SearchTools/search.asp?keywords=xandros&image1.x=0&image1.y=0)

---

### Post by megalomaniac on 2006-06-22
[quote=cprise]Hi. I'm here trying out ubuntu as well.


Xandros Linux will setup a VPN connection to a Windows network automatically. ExtremeTech discusses it here:

[http://www.extremetech.com/article2/0,1697,1738521,00.asp]("http://www.extremetech.com/article2/0,1697,1738521,00.asp")


The Xandros editions that support this feature are SurfSide, Deluxe and Business. TigerDirect has SurfSide at $29 after rebate (pretty decent since you get a USB headset setup for Skype in the box).

[http://www.tigerdirect.com/applications/SearchTools/search.asp?keywords=xandros&image1.x=0&image1.y=0]("http://www.tigerdirect.com/applications/SearchTools/search.asp?keywords=xandros&image1.x=0&image1.y=0")[/quote] 
I'd really rather do it in Ubuntu if possible? Paying for an OS is something I'm looking to avaid as I'm a university student so money is rather tight, hence the move away from Windows, besides I don't think TigerDirect ship to the UK ;). To be honest I don't mind learning how to do things without flashy wizards etc. I just need someone to point me in the right direction...

---

### Post by megalomaniac on 2006-06-23
Had another trawl around the forums and google for some answers I can understand, but no luck :-(. I'm pretty sure the VPN's connected ok, so I guess my problems just what to do after that with the other settings (Routing etc.) and remote desktop. I can't seem to find a decent guide about what's needed and what it all means.
 

 I guess this sort of thing's why a lot of people don't switch to Linux or still dual boot to Windows if they do. I'd really like to get this working in Ubuntu if possible as I really like it, plus as mentioned previously I haven't got the cash to splash out on fancy expensive operating systems. Besides I really don't like some of the directions M$ are taking with Vista, so better to jump ship now before XP's totally obsolete.
 

 Cheers

---

### Post by cprise on 2006-06-24
These two howtos describe how to set VPN routing:

[http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html](http://www.itservices.ubc.ca/support/service/vpn/linuxvpn.html)

[http://linux.ncl.ac.uk/vpn/](http://linux.ncl.ac.uk/vpn/)

---

