---
title: "Trying to figure this one out..."
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by ghost25 on 2011-05-14
Okay, so I've got a rather unique situation amongst Ubuntu users.

I've got a desktop running Netbook Remix (it's slow enough that it can comfortably run Netbook, but not Natty Narwhal) which is connected to a wireless/wired router. Linksys WRK54G if it makes a difference... I don't think it should. I also have an HTC Aria running 2.1, update 1 on it, through AT&T, which I haven't yet rooted. I'm honestly kind of afraid to, since it is a nice little phone, and I've never rooted a phone before... either way, rather I would say irrelevant to the situation.

Either way. I've got DAAP running on both devices, the actual DAAP application running on my phone from the Android Market and the DAAP plugin going in Rhythmbox. I set up the Rhythmbox plugin according to what I needed, and I set up the DAAP app through the phone as well as I know how. This, however, is where I'm getting stuck.

I should note here that I have little knowledge in setting up remote access in Linux, I had SSH set up with a previous laptop but that one is dead so I don't even have that for reference any more.

So. Typing in ifconfig -a, I acquired my IP address, the standard 192.168, as well as my HWaddr (I think this is synonymous with MAC?) being the usual XX:XX:XX:XX:XX:XX bit. I believe my hostname is the usual user@computername, where my hostname is "computername" and I've input this in the DAAP app on the phone. On the phone, I've set the remembered server as "MAC address:8000" called "computername" but when I go to actually access it, it times out.

I've also tried accessing this setup from my mobile browser, but it never loads. I've let it sit for 10 minutes, and nothing happens. I would like to be able to control Rhythmbox from my phone, as the phone is connected to my wireless network and I know, in theory, it should work. But, as is usually the case, theory almost never works the same way in practice.

I'm really not sure at this point what I need to do, or what I need to look for. Like I said, I would like to be able to be in another room and switch songs from my phone on my computer, but I have no idea any more how I would go about this. For all I know, this might not even be doable unless I root my phone... I am gonna need to do this anyway, so I can delete some apps that I never use lol!

Please let me know if you need any more information, and I'll get it posted ASAP. Thanks for any ideas you might be able to send my way.

---

### Post by redmk2 on 2011-05-15
> **ghost25 said:**
> Okay, so I've got a rather unique situation amongst Ubuntu users.
...
So. Typing in ifconfig -a, I acquired my IP address, the standard 192.168, as well as my HWaddr (I think this is synonymous with MAC?) being the usual XX:XX:XX:XX:XX:XX bit. I believe my hostname is the usual user@computername, where my hostname is "computername" and I've input this in the DAAP app on the phone. **[COLOR="Red"]On the phone, I've set the remembered server as "MAC address:8000" [/COLOR]**called "computername" but when I go to actually access it, it times out.

In TCP/IP networking you never ***directly*** use a MAC address to connect to to a host (computer).  You would use the IP address or the DNS hostname.  The protocol ARP resolves the IP to MAC address mapping. I assume that the :8000 part is the port number.  This further leads me to think you need to use either the hostname or IP address as the port number is really TCP port number **not a MAC port number ** (i.e Should be either a [COLOR="Blue"]IP address: port number[/COLOR] or [COLOR="RoyalBlue"]hostname: port number[/COLOR])  > 

I've also tried accessing this setup from my mobile browser, but it never loads. I've let it sit for 10 minutes, and nothing happens. I would like to be able to control Rhythmbox from my phone, as the phone is connected to my wireless network and I know, in theory, it should work. But, as is usually the case, theory almost never works the same way in practice.

I'm really not sure at this point what I need to do, or what I need to look for. Like I said, I would like to be able to be in another room and switch songs from my phone on my computer, but I have no idea any more how I would go about this. For all I know, this might not even be doable unless I root my phone... I am gonna need to do this anyway, so I can delete some apps that I never use lol!

Please let me know if you need any more information, and I'll get it posted ASAP. Thanks for any ideas you might be able to send my way.

Use a hostname as it's more consistent if the IP address is handed out by DHCP.  The IP address can change.  Hopefully the hostname will be always mapped to the correct IP address via the routers DHCP/DNS servers.

---

### Post by ghost25 on 2011-05-20
Really? What would I be using the MAC address for then? That kinda makes me wonder if I've been doing my "security" on my old router wrong then... that one (I got rid of it, too many bugs in the firmware) the only way I could allow everyone to securely connect (I had a desktop plus my Ubuntu laptop connected, laptop being WiFi, plus my roommate's laptop [running Windows 7], his PS3, and our smart phones connected) was to enable a so-called white list... if your MAC address wasn't on my list, you couldn't connect at all.

Seems there's so much more to this than I initially thought... can you point me to a good, idiot-proof tutorial or Wiki for something like this?

And thanks for your reply redmk2, much appreciated.

---

### Post by redmk2 on 2011-05-21
> **ghost25 said:**
> Really? What would I be using the MAC address for then? That kinda makes me wonder if I've been doing my "security" on my old router wrong then... that one (I got rid of it, too many bugs in the firmware) the only way I could allow everyone to securely connect (I had a desktop plus my Ubuntu laptop connected, laptop being WiFi, plus my roommate's laptop [running Windows 7], his PS3, and our smart phones connected) was to enable a so-called white list... if your MAC address wasn't on my list, you couldn't connect at all.

Seems there's so much more to this than I initially thought... can you point me to a good, idiot-proof tutorial or Wiki for something like this?

And thanks for your reply redmk2, much appreciated.

The MAC address is the ID of the Network Interface Card (NIC).  The MAC address is NOT the address of a host that you use to contact another host directly.  If you replace the NIC the MAC address changes.  

When you contact a another host (i.e ping or HTTP etc) you do so by IP address.  ARP is the protocol that TCP/IP uses to ultimately deliver the data to a specific host.  "The Address Resolution Protocol (ARP) is a computer networking protocol for determining a network host's Link Layer or hardware address when only its Internet Layer (IP) or Network Layer address is known." See [**_here _**]("http://en.wikipedia.org/wiki/Address_Resolution_Protocol")for more details.

The MAC address can be used to filter hosts, but it is really not very secure.  MAC addresses can also be spoofed.

In this case I assume your phone is a host in an IP network and as such *[COLOR="Blue"]talks TCP/IP[/COLOR]*.

I guess the question is really: what do you mean by ***[COLOR="Purple"]"On the phone, I've set the remembered server as "MAC address:8000" called "computername""[/COLOR]***?  What does the ***[COLOR="Purple"]:8000 [/COLOR]*** mean?  How are you using this in your phone?

---

### Post by ghost25 on 2011-05-22
Well, what I'm trying to do is, since I keep my desktop on 24/7, I want to use that to store all my music, and access it from different devices remotely. 

I had mentioned that I was using DAAP (which is available from the Android Market), and the way I tried to set it up was "XXXXXXXXXXXX:8000" called "gabe-desktop" so it hopefully could have accessed, as you put it, the NIC. That one failed, I guess.

When I opened the DAAP "Add Server" interface box on the phone, it gives me a few boxes to fill in data; one is for "DAAP Share Name", one is "URL and Port" which by default for some reason is 3689, then there's an option for Login Required which can be checked (if it's checked, then obviously you need to enter a password to access the machine). 

I was trying to set it up according to the FAQ that's listed for the DAAP program, and they said that's how I was supposed to do it.

I guess I don't really NEED to use this particular program, but I would still like to be able to interface with my desktop from my cell phone and control the music rather than have to go halfway across the house to change a track. I figure it should be doable, since the desktop plugs into the same WiFi router that services the rest of the house; everything else accesses the router by WiFi so yeah.

I dunno; I've tried a few different programs to do this, and every well I've drilled has come up dry. Maybe this is something I'll have to learn how to write custom code for, or something... I'll come back here and post the link to the FAQ I was using if I can find it again.

---

### Post by redmk2 on 2011-05-23
> **ghost25 said:**
> Well, what I'm trying to do is, since I keep my desktop on 24/7, I want to use that to store all my music, and access it from different devices remotely. 

That's a nice idea.> 

I had mentioned that I was using DAAP (which is available from the Android Market), and the way I tried to set it up was "XXXXXXXXXXXX:8000" called "gabe-desktop" so it hopefully could have accessed, as you put it, the NIC. That one failed, I guess.

When I opened the DAAP "Add Server" interface box on the phone, it gives me a few boxes to fill in data; one is for "DAAP Share Name", one is "URL and Port" which by default for some reason is 3689, then there's an option for Login Required which can be checked (if it's checked, then obviously you need to enter a password to access the machine). 

I was trying to set it up according to the FAQ that's listed for the DAAP program, and they said that's how I was supposed to do it.

The "URL and Port" is the key to connectivity. This is a common URL format```
http://www.example.com
```In fact this also implies the port too.  The entire URL : port is```
http://www.example.com:80
```

It sounds like you are supposed to be contacting a a small web server and reading a web page.  Maybe with Hyperlinks? 
> 

I guess I don't really NEED to use this particular program, but I would still like to be able to interface with my desktop from my cell phone and control the music rather than have to go halfway across the house to change a track. I figure it should be doable, since the desktop plugs into the same WiFi router that services the rest of the house; everything else accesses the router by WiFi so yeah.

I dunno; I've tried a few different programs to do this, and every well I've drilled has come up dry. Maybe this is something I'll have to learn how to write custom code for, or something... I'll come back here and post the link to the FAQ I was using if I can find it again.
It would be nice to see the documentation your are referring to.  What is the name of the DAAP application?

---

### Post by ghost25 on 2011-05-23
The application I'm *trying* to use is called "DAAP Media Player". Here's a link to it... [https://market.android.com/details?id=org.mult.daap&feature=order_history](https://market.android.com/details?id=org.mult.daap&feature=order_history) and here's the actual project page: [http://code.google.com/p/daap-client/](http://code.google.com/p/daap-client/)

---

### Post by redmk2 on 2011-05-23
> **ghost25 said:**
> The application I'm *trying* to use is called "DAAP Media Player". Here's a link to it... [https://market.android.com/details?id=org.mult.daap&feature=order_history](https://market.android.com/details?id=org.mult.daap&feature=order_history) and here's the actual project page: [http://code.google.com/p/daap-client/](http://code.google.com/p/daap-client/)

As I thought.  You need to use the IP address: port number or hostname: port number -- NOT the MAC address to connect your phone to the DAAP server.  In fact, looking at the video that is on the developer's page the client should search for the server and try to connect.

The exact method might be dependent on the specifics of the DAAP server.  When you re-discover the Howto you were using we can go further than this.  I don't have an Android phone so I have no direct experience with the app.  FYI the developers are 2 brothers named Miceli.  They have listed their email and encourage users to interact with them.  Now that is direct access.  Chris Miceli has his own [**_[COLOR="DarkSlateGray"]blog site [/COLOR]_** ]("http://chris-miceli.blogspot.com/2010/05/daap-android-client-updates.html")for the Android DAAP-client and you can contact him there

---

### Post by ghost25 on 2011-05-29
Thanks a lot redmk2, that does make more sense now that you point it out. I kinda thought I was doing it wrong when I tried using the MAC address to make it work! I didn't see any video on the dev page though, is that on the Google Code page, or the actual app page?

I'll also try firing him off an email tomorrow, hopefully then we can get this figured out. Thanks again!

---

### Post by ghost25 on 2011-06-04
Well, I can't quite mark this thread as "Solved," but I did manage to find a good web site that would be a great help to anyone else who might be struggling with DAAP. [http://www.linuxjournal.com/content/introducing-simplify-media](http://www.linuxjournal.com/content/introducing-simplify-media) I'm going to keep hammering on this one, and hopefully I can get it figured out.

EDIT:

Well, I finally got this one licked. For now, anyway.

It might sound odd, but how I got it figured out was to visit this site, [http://www.navarin.de/projects/rbox/](http://www.navarin.de/projects/rbox/), and I ended up downloading a .py script that, once installed from my default Downloads folder, opened up port 8484 and it was literally so simple that a complete newb could do it in 10 minutes. It's technically done through an app in the Android Market called Banshee Remote, found here, [https://market.android.com/search?q=Banshee+Remote&so=1&c=apps](https://market.android.com/search?q=Banshee+Remote&so=1&c=apps), and even though the app claims to only work for Banshee, I have Banshee closed completely on my desktop (this is, again, where all my music is stored). It still runs through Rhythmbox.

If anybody has any questions specifically as far as how I got this to work, post 'em here, and I'll try to answer to the best of my ability.

---

