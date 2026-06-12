---
title: "The right setup for Ubuntu / WinXP?"
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by BigMike on 2006-05-18
Hello friends,

I've been working on this for hours and hours... but not having much luck.

I just set up Ubuntu, and I'd like it to be my network firewall.  Basically, I have an XP box that I'd like to protect a bit better and so I'd like all my internet access to be routed through through this nix box.  I actually have several other XP boxes, and if it isn't too difficult, I'd eventually like to route them through the Ubuntu box as well (but that part isn't a real priority just yet... right now I'm just focusing on protecting my main XP box)

Here's the config:

Both my XP and nix boxes are connected to the router.

My Ubuntu box has 2 NICs, and I have one of those NICs (eth0) plugged into that router (eth0 is configured for DHCP).   The 2nd NIC is is configured for a static IP.

Firestar is installed and appears to be running correctly.

Now, I'm thinking that I could connect my XP box to the 2nd NIC on the nix box and get access that way.  Although, I'm not sure if that requires a crossover cable (I can make one if needed).

Is that the right way to set it up?  Or, is it possible to have my XP box connected to the router, then the router connects to one NIC on the nix box, and the other NIC plugs directly into the cable modem, then point my XP NIC to the static IP of that 2nd NIC?

I've never set anything up like this before, so it's a bit confusing.  My 'guesses" above could be way off.  :p  I have plenty of NICs, routers, cables, etc... so hardware availablilty isn't a problem.

I have no preference on how things are set up... I'm just trying to beef up the security of my XP box(es).

Any suggestions are truly appreciated!

---

### Post by matthew on 2006-05-18
[quote=BigMike]
Here's the config:

Both my XP and nix boxes are connected to the router.

My Ubuntu box has 2 NICs, and I have one of those NICs (eth0) plugged into that router (eth0 is configured for DHCP).   The 2nd NIC is is configured for a static IP.

Firestar is installed and appears to be running correctly.

Now, I'm thinking that I could connect my XP box to the 2nd NIC on the nix box and get access that way.  Although, I'm not sure if that requires a crossover cable (I can make one if needed).

Is that the right way to set it up?  Or, is it possible to have my XP box connected to the router, then the router connects to one NIC on the nix box, and the other NIC plugs directly into the cable modem, then point my XP NIC to the static IP of that 2nd NIC?

I've never set anything up like this before, so it's a bit confusing.  My 'guesses" above could be way off.  :p  I have plenty of NICs, routers, cables, etc... so hardware availablilty isn't a problem.

I have no preference on how things are set up... I'm just trying to beef up the security of my XP box(es).

Any suggestions are truly appreciated![/quote]Actually, your understanding seems pretty sound. You have several options, all of which should work. I would lean toward this:

Plug your Ubuntu box directly into the cable modem. Make sure it is working well.

Use Firestarter to configure port forwarding and to allow those services through that you want going through. 

Plug the XP box into the second nic on your Ubuntu box. Configure it for a static IP. Configure the second nic on the Ubuntu box the same way.

That should do it. Once you get it running you will have enough experience to plug the router into the Ubuntu box and the XP computers into the router if you wish.

I wrote a howto a while back on a specialized networking case. It isn't quite the same as what you are doing, but it is similar and will give you some ideas on configuring your specifics. Take a look and see if it helps you.  [http://ubuntuforums.org/showthread.php?t=76346](http://ubuntuforums.org/showthread.php?t=76346)

---

### Post by BigMike on 2006-05-18
Thanks for the great input, Matthew!

I'll probably go ahead and try to set up the entire network through it from the get go then since the nix box will have the only connection to the modem.

So here's what I've gathered... I've got the Ubuntu box going straight into the modem, then I guess my router should be connected to the 2nd NIC on the nix box, and then the rest of the network can connect through the router.  Then all my 'other' boxes will point to that static ip.

But how do I set up port forwarding with Firestar?  Firestar, of course, doesn't have a "port forwarding" tab (heh heh... that would be too easy!)  :P  

I've never actually set up forwarding before.  Yikes!.. I hope that doesn't make me a noob!  (ugh!)  :P

Thanks!

Mike

---

### Post by matthew on 2006-05-18
[quote=BigMike]Thanks for the great input, Matthew![/quote]You are welcome. Glad I can help out whenever possible. 

[quote=BigMike] I'll probably go ahead and try to set up the entire network through it from the get go then since the nix box will have the only connection to the modem. 

So here's what I've gathered... I've got the Ubuntu box going straight into the modem, then I guess my router should be connected to the 2nd NIC on the nix box, and then the rest of the network can connect through the router. Then all my 'other' boxes will point to that static ip.[/quote]Your plan sounds fine. I only suggested starting with the XP computer instead of the router to simplify the process. The router may need a little bit of configuring itself to work...just so you know in advance. If you only plug the XP computer into the Ubuntu computer at first you will minimize troubleshooting. Once that is running it will be easier for you to add the router/other computers later. It's just something to consider. Either way should be fine.

[quote=BigMike] But how do I set up port forwarding with Firestar?  Firestar, of course, doesn't have a "port forwarding" tab (heh heh... that would be too easy!)  :P  [/quote]Let me confirm...you mean "Firestarter," right? I can't recall a program called "Firestar" so it's probably just a typo but I want to be sure we are talking about the same thing.

Preferences->Network Settings
  -select the first nic that the modem is plugged into as your "Internet Connected Network Device"
  -select the second nic that the router will go into as your "Local Network Connected Device"
  -select "Enable internet connection sharing"
  
[quote=BigMike] I've never actually set up forwarding before.  Yikes!.. I hope that doesn't make me a noob!  (ugh!)  :P[/quote]We all start somewhere. I learned how to do this not long before I wrote the how-to. :) That's the fun of these forums--you don't have to know everything. Share what you know and feel free to ask about the stuff you don't know.

---

### Post by BigMike on 2006-05-18
Heh heh! (Firestar/Firestarter)... the noob in me has clearly shown through!  :P

Okay, sounds like I've got my work cut out!  Well, with a bit of luck I'll hopefully have this figured out today.  And if I'm really lucky, I'll be a nix guru by this evening! (not holding my breath on that one).

I've been using Windows since 95, so it's quite hilarious almost none of my experience can be applied to the Linux world.  Heck, it felt like an accomplishment just figuring out how to install various packages.  Ugh!  (I can't believe I'm even saying that!)

Anywayz, off to the project!  Thanks for all your help!

Mike

---

