---
title: "Mythtv software remote"
date: 2008-09-03
forum: Mythbuntu
---

### Post by awilisch on 2008-09-03
Every time I look for posts on remote controlling a mythtv box I get responses for remote controls. I'm curious though if anyone knows of a piece of software that would run on a laptop that could remotely control a mythtv box?

My server is in the back room and I'm building a front end to plug into my TV. I almost always have a laptop next to my couch so I figured it might be easier if I could find a program that would run on my laptop where I could connect up to a front end (living room, bedroom, basement, whatever), then pick what I want to display and start it playing on the tv the front end is plugged into rather than on the laptop.

I've been using mythtv-player to play back on my laptop, which is what got me thinking about what if it could remote control the front end rather than just do playback.

Just a thought. I'm curious about what others think.

--Aric

---

### Post by volkswagner on 2008-09-03
There is a remote control in mythweb.  I do not have it setup, nor have I used it.

You can search "mythweb remote control", for some instructions.

Edit: I think you need to enable it within each frontend first.

---

### Post by bmwman on 2008-09-03
Why don't you use Remote Desktop? I also have my laptop by the coach and I use it to  control my HTPC if i want to do  something that I can't do with the remote.

---

### Post by deadcyclo on 2008-09-04
Or if you like doing stuff command line you can [telnet xxxxxx 6546](http://www.mythtv.org/wiki/index.php/Telnet_socket)

---

### Post by mark467 on 2008-09-04
I have a similar set up and would love to get the web based remote to work. I enabled it in setup I think but it dosent work. More info would be great. I use VNC / remote desktop and it is bulky and slow with the screen updates.

when i try the web remote i get a msg saying no frontends have been selected (even when i click to select it on right side)

---

### Post by Archmage on 2008-09-04
Sorry, but I'm not exactly getting what do you want.

You have a front end that is displaying the movies on the TV, right?

And you want a second PC to remotly control your front end? Why aren't you using a remote control that is pluged into the front end?

Or simply use a keyboard (infrared?).

---

### Post by volkswagner on 2008-09-04
> **mark467 said:**
> I have a similar set up and would love to get the web based remote to work. I enabled it in setup I think but it dosent work. More info would be great. I use VNC / remote desktop and it is bulky and slow with the screen updates.

when i try the web remote i get a msg saying no frontends have been selected (even when i click to select it on right side)

I too enabled network remote control in the frontend.  I think this is for the telnet option.

When I go into mythweb and select remote, I see my frontend listed.  I select the frontend and get an error that the frontend is not responding.  

I opened port 6546 on my router, but no change.  

EDIT:  I tried editing the port used.  I also added my Master BE/FE machine.  Both machines show on the list of avail frontends to choose for he remote feature.  I tried changing the port to 8080 on my master.  The only difference is it takes longer for the error to display "frontend not responding".  So it may be a port issue or some added config is needed.  I don't see much information on this feature.

What port does the mythweb remote work on?

It should also be noted I am running mythweb on port 8080.  Could this be an issue?

---

### Post by MikeNick42 on 2008-09-04
Synergy may be an option for what you want to do. It'll let you use the laptop and mouse on your laptop to control the frontend computer without all the overhead of remote desktop.

---

### Post by deadcyclo on 2008-09-04
I took a quick gander at the source. It's really a "quick hack job". I could make something much better in an evening :D

It connects to localhost port 6546 so it's not an issue with your router or the port.

One thought that I had. Did you restart mythfrontent after enabling the remote port? I'm pretty sure I had to do that before telnet worked.

---

### Post by Boppy3125 on 2008-09-04
> **MikeNick42 said:**
> Synergy may be an option for what you want to do. It'll let you use the laptop and mouse on your laptop to control the frontend computer without all the overhead of remote desktop.

I tried that and it was pretty good.  One problem I solved is that I discovered I needed to create static IP address for the laptop when I hadn't previously.  I couldn't get it to resolve by name.  At least I think I needed to specify the machine from both directions, but it is possible I am mis-remembering.

My one problem I didn't like and didn't work around, after I was done and brought my mouse back to the laptop's desktop, MythTV lost focus.  It just acted a little weird when I was done.  I found that I would work on things for awhile, and then when ready to go to bed I would reboot and not restart Synergy.

---

### Post by mark467 on 2008-09-04
well if anyone knows of documentation for the web based remote for mythweb or knows how to get it working i wouldf love to know. it seems it would be a good solution for me. i have tried to get to remotes ( ATI & Pinacle) working with no success.

---

### Post by deadcyclo on 2008-09-04
Boppy3125: The laptop you want to control myth from, is it running windows or linux?

---

### Post by Boppy3125 on 2008-09-26
> **deadcyclo said:**
> Boppy3125: The laptop you want to control myth from, is it running windows or linux?

Didn't subscribe so didn't notice the follow-up.  It is windows.

---

### Post by volkswagner on 2008-12-24
Does anyone have this working?  Got any tips if you did get it working?

I am really interested in this project.  I am surprised others are not.

I think it would be really cool to control a frontend with a web enabled phone.  I almost always have my phone on me.  It would work from other rooms or even other states (is there a ghost in the house???? LOL).

---

### Post by Ohs0Ahxi on 2008-12-24
I've set up _[this](http://www.mythtv.co.nz/mythtv/remote/index.html)_ and used a couple of times when my remote stopped working. It works fine from my laptop i cant remember if i ever got around to trying it from my phone, there is a PDA version.

---

### Post by volkswagner on 2009-04-26
> **Jenko22 said:**
> I've set up _[this](http://www.mythtv.co.nz/mythtv/remote/index.html)_ and used a couple of times when my remote stopped working. It works fine from my laptop i cant remember if i ever got around to trying it from my phone, there is a PDA version.
 
I tried using the remote provided from the above mentioned link.  I got errors, maybe it is not supported by mythtv .21 since it predates 2007.

I did however get the included mythweb remote working.  I believe it is related to Java on the client browser.  The only thing I can think that is different from earlier attempts is I have since enabled the Java in firefox.  It was required to get filemanager working in Webmin.  I will need to confirm this since it also worked on my webDT.  I need to verify if Java was enabled on the 'DT.  Perhaps there have been mythtv updates to fix it.

I know this is an old thread but I think this is a great function.  I am after larger buttons because I am trying to use it with a webDT.  The webDT has a touch screen, and I would like to use it without a stylus for convenience.  This would be great for a dark room, no need for a lighted remote control.  :P

---

