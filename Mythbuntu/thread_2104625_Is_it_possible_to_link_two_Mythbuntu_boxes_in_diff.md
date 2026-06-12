---
title: "Is it possible to link two Mythbuntu boxes in different locations together?"
date: 2013-01-13
forum: Mythbuntu
---

### Post by Bullwinkle_Moose on 2013-01-13
I am very new with MythTV and Mythbuntu (less than two weeks). At the moment this is more of a curiosity question than something I plan to do in the immediate future, but I had an interesting thought.

Let's say you have your primary residence in City A and another location (could be second home, office, relative's home) in City B.  And let's say City B has a much better selection of local TV stations.  And let's say that you are using something like a HDHomeRun Dual to receive over-the-air TV at your home, but you only get about ten stations (counting subchannels) whereas your location in City B gets closer to 50 stations, plus it's closer to the transmitters for most of those stations.

So here's what I'm wondering:  It it possible to link two MythTV backends together so that SELECTED programming recorded on the a backend and HDHomeRun in City B could be transferred to the backend in City A and vise versa?

The idea is that if you are at home and you want to watch a program that is only received reliably in City B, you could set up a Mythbuntu backend there, schedule and record it from a station there, then have it transferred to your backend in City A. Conversely, while you are in City B, you could schedule a program in City A (for example, a local news program) and have it sent to the backend in City B.  Note that the idea would be to have only selected programming transferred, not everything that might be recorded on either backend. And you'd obviously want to remove commercials and maybe transcode the programming before sending it across the 'net, particularly if one or both ends has capped internet service.

I realize that there would probably be some way to hack this functionality by setting up a script to look for and transfer files, but that's not what I'm asking.  I'm asking if the MythTV backend software itself has any built-in capability to connect to a peer backend system in another location and schedule and share recorded programming.  Obviously there would be a lot of potential uses for such capability, if it exists!

What would be really great is if a MythTV frontend could show a schedule grid for both systems, and if you schedule an event for recording and it happens to be coming from the remote system, it would give you the option to transfer it to the local backend and delete it from the remote backend (after recording is finished), transfer it but also leave a copy at the remote, or not transfer it and only leave a copy at the remote.  I suppose I am dreaming, but just thought I'd ask if there was any possibility that such capability might exist.

---

### Post by AlecJ on 2013-01-14
A secondary/slave backend with extra tuners?
yes works well over LAN.
I had this for a while one for Freesat and one for Freeview here in the UK.

All frontends show all the channels/recordings etc that both backends have. i.e like one big backend with 12 tuners
You setup different Video sources for each type on the master backend, in my case 1 Freeview, 2 Freesat HD, 3 Freesat. DVB-S cards crash trying to tune to DVB-S2 channels?

Not possible over the internet yet bandwidth required would be too big. So I'm told, not measured, but my 1Gb can't stream HD to remote frontends.

---

### Post by tgm4883 on 2013-01-14
> **Bullwinkle_Moose said:**
> I realize that there would probably be some way to hack this functionality by setting up a script to look for and transfer files, but that's not what I'm asking.  **I'm asking if the MythTV backend software itself has any built-in capability to connect to a peer backend system in another location and schedule and share recorded programming.**  Obviously there would be a lot of potential uses for such capability, if it exists!

No. And due to the nature of said feature request and the fact most MythTV developers reside in the US, such functionality will probably not be implemented due to legal reasons.

---

### Post by dannyboy79 on 2013-01-14
couldn't you theoretically connect the two locations with a vpn? you could have a transcode job that would transcode the remote locations recordings down to a reasonable size which could be streamed over vpn possibly? Good luck

---

### Post by Bullwinkle_Moose on 2013-01-14
> **tgm4883 said:**
> No. And due to the nature of said feature request and the fact most MythTV developers reside in the US, such functionality will probably not be implemented due to legal reasons.

I'm not sure I understand where you are coming from here.  I can't imagine what "legal reasons" would come into play that don't already exist.  Recording TV shows is not illegal, per the Betamax decision.  The Slingbox exists, so I assume that sending received signals from one location to another for one's own personal use is not illegal.  I realize that local broadcasters and possibly even the networks might hate it if you send a signal received in one market to another, but to my mind that's just the modern equivalent of having someone someone videotape a show for you in one area and then mail the tape to you so you can watch it in another location.  Just because you convert the signal to a digital format and send it to another location over the Internet, rather than depositing it in a mailbox, shouldn't change the legal situation.

I mean, I get that we live in a litigious society, but I don't think that ideas should be thrown out because someone has some nebulous idea that there might be legal issues.  For all I know there may be legal issues with breathing air but people will do it anyway.  Anyway, I would just say that absent someone citing case law that would reasonably apply here AND that would cause a problem for the developer of the software, let's not kill this discussion over a fear of what MIGHT POSSIBLY happen.

(That said, I do understand that this is why so much software development is now coming from outside the USA — it's just that fear of litigation that causes people in the USA to clam up!)

---

### Post by Bullwinkle_Moose on 2013-01-14
> **dannyboy79 said:**
> couldn't you theoretically connect the two locations with a vpn? you could have a transcode job that would transcode the remote locations recordings down to a reasonable size which could be streamed over vpn possibly? Good luck

That might work, although for most users setting up a VPN is not exactly a straightforward process.  The bigger issue would be how to get the remote backend to send ONLY certain traffic (the recorded programming wanted at the other location) over the VPN, while NOT using it for general Internet access.  I don't know enough about VPN's to know if it is possible to direct only certain selected traffic through a VPN tunnel.  My (very limited) experience with VPN's is that it's an all or nothing situation — either all your Internet traffic goes through the VPN (except the VPN packets themselves) or all of it uses the local Internet connection.  I'm guessing there are ways around that, but I'm also guessing that it's not something the average Mythbuntu user would be able to figure out easily.

---

### Post by dannyboy79 on 2013-01-14
primary backend and slave backend functionality already exists in the code, so you just need to create a vpn between the two locations so they appear to be on the same network and you should be good to go

---

### Post by Bullwinkle_Moose on 2013-01-14
> **AlecJ said:**
> A secondary/slave backend with extra tuners?
yes works well over LAN.

.....

Not possible over the internet yet bandwidth required would be too big. So I'm told, not measured, but my 1Gb can't stream HD to remote frontends.

That's why my idea was to record the program on one backend, then after it was recorded, commercials removed (if desired), and transcoded (if desired), only then would it be moved or copied to the other backend.  That would both potentially reduce the size of the recording, and eliminate any issues associated with live streaming.  While I'm sure some types of Internet connections could possibly handle live streaming (FIOS, or Google's Fiber project in Kansas City, maybe) I'm pretty sure I'd have issues with it on my local cable connection, so I wasn't thinking of attempting that.

Anyway, as I say, I was just curious whether Mythbuntu had that capability, and what I'm taking away here is that maybe one could set up a secondary or slave backend (how do you do that?) over a VPN but you'd have to be a fairly advanced Linux expert to make it work, at least the way I had envisioned it.

---

### Post by dannyboy79 on 2013-01-14
there's guides out there already for setting up openvpn as well as guide for setting up a slave backend for mythtv

---

### Post by AlecJ on 2013-01-15
> **Bullwinkle_Moose said:**
> That's why my idea was to record the program on one backend, then after it was recorded, commercials removed (if desired), and transcoded (if desired), only then would it be moved or copied to the other backend.  That would both potentially reduce the size of the recording, and eliminate any issues associated with live streaming.  While I'm sure some types of Internet connections could possibly handle live streaming (FIOS, or Google's Fiber project in Kansas City, maybe) I'm pretty sure I'd have issues with it on my local cable connection, so I wasn't thinking of attempting that.

Anyway, as I say, I was just curious whether Mythbuntu had that capability, and what I'm taking away here is that maybe one could set up a secondary or slave backend (how do you do that?) over a VPN but you'd have to be a fairly advanced Linux expert to make it work, at least the way I had envisioned it.


If you have your frontend/backend setup with mythweb installed, you can do most of what you want, just not inside the frontend.
point another browser on another machine on your LAN at it's IP and then you can stream and/or download recorded programs. Place the downloaded files in the Videos folder of another Mythbox and watch from the videos menu.

If you set a mythweb password and open port 80,22 in your router/firewall to your Mythbox, then using a fixed IP or a rent domain name you can get in from the internet to your box and download, set programs to record and loads of other stuff.
The stream .asx is too slow to watch (here anyway), and the direct download took a few hours for just under an hour of SD.

---

### Post by superm1 on 2013-01-15
I actually just published a blog post on exactly this topic.
[http://supermario-world.blogspot.com/2013/01/multi-homed-mythtv-backend.html]("http://supermario-world.blogspot.com/2013/01/multi-homed-mythtv-backend.html")

I have two homes and only pay for cable in one of them.  I transfer the content from one mythtv backend to the other and insert the recordings into the database.

All the scripts I use to do it are on the blog post.

---

### Post by dannyboy79 on 2013-01-15
> **superm1 said:**
> I actually just published a blog post on exactly this topic.
[http://supermario-world.blogspot.com/2013/01/multi-homed-mythtv-backend.html]("http://supermario-world.blogspot.com/2013/01/multi-homed-mythtv-backend.html")

I have two homes and only pay for cable in one of them.  I transfer the content from one mythtv backend to the other and insert the recordings into the database.

All the scripts I use to do it are on the blog post.isn't that a really long way around the solution? there would be no need for importing videos or sql database entries at all if you just connected the two homes with a vpn correct? Am I wrong here just let me know.

---

### Post by superm1 on 2013-01-15
> **dannyboy79 said:**
> isn't that a really long way around the solution? there would be no need for importing videos or sql database entries at all if you just connected the two homes with a vpn correct? Am I wrong here just let me know.

In an ideal world with good enough bandwidth you're right.  But the upload on both of my connections won't be enough to handle streaming a recording over the web.

---

### Post by Bullwinkle_Moose on 2013-01-16
> **dannyboy79 said:**
> isn't that a really long way around the solution? there would be no need for importing videos or sql database entries at all if you just connected the two homes with a vpn correct? Am I wrong here just let me know.

I will just point out that setting up a VPN is not the easiest thing in the world to do, unless you are already very experienced with them.  I have only tried to set up one in my life and it took me a solid month to get everything working the way I needed it to and I can honestly say it was the most difficult thing I have ever tried to do with a computer.  That was using OpenVPN, by the way.  Maybe things are easier now but if so I'd be surprised.  And once I got it working it still never really worked entirely as if both ends were on the same network - for example you could not see networks shares on the opposite end of the tunnel, though you could connect to them if you knew the local IP address.  I was so frustrated by that whole experience that I said I'd never do anything like that again!

Please remember that there are many of us who use Mythbuntu or Ubuntu that have primarily used Windows and have never really got into the truly "geeky" stuff in Linux, and about the only thing we really know about networking is how to hook up a consumer-grade router.  In fact one of my complaints about MythTV is that the backend offers far too many options, most of which should be hidden behind an advanced settings tab because the average user is probably going to leave at least 90% of them on the defaults.

In my situation I'd be much more likely to use SSH to transfer files, or even to set up a tunnel to the web page server on the distant side.  For limited connectivity SSH is probably much easier to set up and configure than a VPN.  At least it would be for me.

---

### Post by Ubu_Fester on 2013-01-16
This quote really hit home:
> Please remember that there are many of us who use Mythbuntu or Ubuntu  that have primarily used Windows and have never really got into the  truly "geeky" stuff in Linux, and about the only thing we really know  about networking is how to hook up a consumer-grade router.  In fact one  of my complaints about MythTV is that the backend offers far too many  options, most of which should be hidden behind an advanced settings tab  because the average user is probably going to leave at least 90% of them  on the defaults.I agree.  I am considered a defacto computer expert across my circle of friends (ok, my mother), yet I am not confident that my Myth box will continue to run through the year.  ...about 25% of the time the update process breaks something...  and last week, a number of scheduled jobs have errored out "program not available" -- I checked the logs but see no clear problem...  It's frustrating.

> In my situation I'd be much more likely to use SSH to transfer files, or  even to set up a tunnel to the web page server on the distant side.   For limited connectivity SSH is probably much easier to set up and  configure than a VPN.  At least it would be for me.This (comment) is something I'd like to do -- Currently I can connect my Windows 7 box within my LAN, but would like to connect from internet to my box to check up on upcoming recordings, etc.

---

### Post by dannyboy79 on 2013-01-16
> **Ubu_Fester said:**
> This quote really hit home:
I agree.  I am considered a defacto computer expert across my circle of friends (ok, my mother), yet I am not confident that my Myth box will continue to run through the year.  ...about 25% of the time the update process breaks something...  and last week, a number of scheduled jobs have errored out "program not available" -- I checked the logs but see no clear problem...  It's frustrating.

This (comment) is something I'd like to do -- Currently I can connect my Windows 7 box within my LAN, but would like to connect from internet to my box to check up on upcoming recordings, etc.
if you just want to check on upcoming recordings you could install mythweb and ensure the proper port is forwarded in your router. or maybe look into mythtv-status, it can be run from a command line via ssh into the server.

No one said these solutions were easy to implement. there is such a great community of users, a ton of guides written, IRC channels, and of course this forum to assist when we can. If you don't feel it's worth your effort to get the awesomeness of mythtv and you just want an easy solution, then maybe like the masses and just pay for it from your cable provider.

I don't mean to sound so harsh but it's a reality. The developers do the best they can to make it as easy as possible, heck mythbuntu didn't even exist originally, you had to figure out how to install mythtv yourself on top of whatever linux distro you ran.

---

### Post by Ubu_Fester on 2013-01-16
I've had the box running for 3 years now.  I'm committed.  

...But I've spent more time (than I thought I would) troubleshooting want appears to be "random" issues....

---

### Post by dannyboy79 on 2013-01-16
> **Ubu_Fester said:**
> I've had the box running for 3 years now.  I'm committed.  

...But I've spent more time (than I thought I would) troubleshooting want appears to be "random" issues....
Yeah, I hate those times and in fact I am in just that situation right now. I can't access mythweb and for some reason my mythbackend keep being terminated by code 251 and it retarts only to be terminated again.

SO I have some serious digging to do and yes it pisses me off for sure as I don't even recall doing any updates and it's even more of a pain because it's a headless server so all my work is done thru ssh BUT it just allows me to learn the more inner workings of everything.

It sucks BUT then again, it's FREE software.

---

### Post by Ubu_Fester on 2013-01-16
[SIZE=3][COLOR=Blue]Yes, *Exactly!*  [/COLOR][/SIZE][SIZE=4] :)[/SIZE]

---

