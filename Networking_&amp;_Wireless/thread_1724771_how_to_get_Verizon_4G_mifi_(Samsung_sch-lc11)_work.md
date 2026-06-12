---
title: "how to get Verizon 4G mifi (Samsung sch-lc11) working"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by mgmiller on 2011-04-08
I recently upgraded myVerizon wireless  mifi hotspot card from a Verizon 5 spot 3G unit to the new Samsung SCH-LC11 4G mifi hotspot.  The old 3G device was very reliable out of the box.  No wifi connection problems at all.

The new 4G device was a constant headache.  The wifi would connect and disconnect over and over again.  Sometimes it would stay connected for a few minutes, but then the problems would start again.  Totally unusable in Ubuntu.  I tried both 10.04 and 10.10.  

Annoyingly, it worked just fine in Windows XP.  The Verizon people were not really helpful.  They suggested resetting the device, etc.  Things I had already tried.  After they consulted with their "tech experts"  they concluded that they don't support Linux and gave me the option of returning the device.

Here's what I finally figured out.

First, you need a Windows or mac box to connect to the device via wifi.  
Open a browser and go to 192.168.1.1
At the log in page, enter the same password that you used to connect to the device in Windows or Mac.  It is also printed on a label above the battery.  You can see it after you remove the battery cover.

Click on the "Network" tab at the top of the screen.
Below that where it says LAN WiFi, click the WiFi button
Click the "Manual Configuration" button.
On the "Security" line click the drop down where it says WPA/Personal/PSK (TKIP)
Change this to WPA2/Personal/PSK (AES)
The password field just below it will now be blank.  Simply reenter the same password that you used before.
Click "Apply" at the bottom of the page.
It will also warn you that you have not changed the profile name and you should delete the profile from whatever Windows was using to ID the device.
You will probably lose the connection.

Return the Windows/MAC box to the owner and say thank you.

Boot up your Ubuntu box and it should just work.

I posted this how to using the device just now.
It's pretty fast, speedtest.net tells me i am getting 18.75Mb down x 4.75 Mb up.  latency is about 85 ms.  Not too shabby.

Since I got my device at a Verizon store, and they set it up for me while I was there, had I known about this, I could have done all the setup at the store and been ready to go as soon as I got home.

Enjoy.

Edit:
I also realized I had changed the hotspots 802.11 settings from b/g/n  to just b/g, so I tried turning the "n" part back on to see what happened.  Since my notebook is only b/g, it took a little longer for my computer to reacquire the hot spot, and its resulting connection varied from 1Mb to 54Mb.  It did not drop the wifi connection though.  I set it back to b/g only and the wifi connect is almost instant and stays at 54 Mb.  Since I don't own any 802.11 n hardware, I'll just leave it this way for now.

---

### Post by joshe1313 on 2011-08-16
Thanks a million - your a lifesaver!

---

### Post by dArksp0re on 2011-08-27
Brilliant post!  Thank you! :P

---

### Post by ddettore on 2011-09-21
Great job - how come verizon and samsung don't know this

Ubuntu Rocks!

---

### Post by mgmiller on 2011-09-21
I posted the same how to on the Samsung site for this device.  Why don't they know?  As soon as they hear "Linux", their eyes glaze over and they start to drool.  Their only responses are, "we don't support Linux, return the device for a refund".  I suspect that is what their trouble shooting software tells them to say.

Hopefully as Google Chrome and Android continue to pick up market share, their attitude towards Linux may change.

---

### Post by hammer13 on 2012-01-09
Thanks so much this was driving me crazy. If anyone wants to give a technical breakdown why changing that setting would fix the problem I would love to learn

---

### Post by WindingRoad on 2012-02-21
I noticed you are the last to post on this thread.  I hope you can help me with a question about something the OP posted.   What is a "mac box" and where do I get one.  Can you explain what the OP means by hooking it up.  I hate this Verizon MiFi thingy and would love to get it working. I'm computer illiterate so can you be very specific on what to do. I'd really appreciate it.  Thanks so much for your time.

WR,,, three commas for Becca


Edited for grammer mistake.

---

### Post by mgmiller on 2012-02-22
A MAC box is simply a computer running apple OS.  You can use any computer running apple os or windows.  They will need to make the connection to the mifi by wifi.  Failing access to one of the above, I suggest you print out the instructions at the beginning of the post and bring them to your Verizon store.  They can easily make the change for you.  Before I figured out how to resolve this, my Ubuntu laptop did occasionally make a solid connection to the samsung mifi.  If yours ever does seem to connect and stay connected, you can do the change at that time.

---

### Post by WindingRoad on 2012-02-22
So if I have a MacBook Pro I can just do from "open your bowser" etc.  Remember I'm very computer illiterate.  I also looked in App... Utilities... Network Utilities.... The Airport and found I was getting 54mbits/s and then a/g/g/n    Thanks for replying.  I want to finish a movie.  LOL.

PS.  When I get to Security I don't find a drop down. It asks for a password and to change the password.  HELP.............  NO WPA/Personal/PSK (TKIP)   etc.


2 hours later. I went back onto the site and saw security down the page. I was clicking on Security at the top of the page beside Network.  My MiFi is running faster.  Dropped once in the last 2 hours.  Better than before.  I really do appreciate your tolerance and help... Great info.  I outta go over to Verizon and show them how to do their job.  LOL   60 year woman showing up geeks.  LOL

---

### Post by mgmiller on 2012-02-23
Glad you got it working from your mac Book Pro.  Be aware that after you change the settings, the profile for that device in your mac book may stop working.  If so, you will need to go back the network utilities area where you saw it before and just delete the samsung device.  Your mac book should then see it with the new settings and reconnect without problems.

---

### Post by WindingRoad on 2012-02-26
Good Morning,  Hope you are doing well.  I have a couple of questions for you.   Should I be running something other than Safari?  Came with my MAC.  I went to a site that tell me how many GB's I'm using for various type of surfing etc.  Says I can watch 6 stream vids a month with NO other internet actions.  Bummer.  I have Amazon prime so I can stream some fairly new movies. I have no TV, so I like watching on either my Fire or here on the 17" MBP.  My other question is:  Will my MiFi be faster and more reliable when we get 4G around here?   I'm  thinking of signing off Verizon and paying the $$ and going to a good local company.  GWI if you want to see what they have for offer.  I really do appreciate your helping me it's made a world of difference.  

Oh dear I thought of something else.  After I load an internet addy the MiFi can be slow loading.  As soon as I move my cursor from the addy space and onto the white window the page loads pretty quickly?  Is that a Safari thing?  I've been emptying my history and cache on a regular basis.  History every hour or so.  Yes, I know I surf too much.  And cache maybe every other day or so.  

Geeez maybe I should start all over with this computer stuff and go to come kind of class.  <VBG>  Again thanks for your help.

---

### Post by mgmiller on 2012-02-26
I'm afraid I have no experience with Safari as it's a MAC only browser, as far as I know.  

Please note that all the following speeds are obtained with Verizon 3G and Verizon 4G LTE connections.  If you use another carrier, you will get different results.....

I suspect most of your speed issues are caused by only having a 3G connection.  When I switched from 3G to 4G on Verizon, the speed difference was amazing.  from my perspective, having a 3G internet connection was only a sort of "proof of concept" thing for me.  It allowed me to do basic things, but it was very slow ( around 0.9-1.0 Mb/down by 0.3-0.7 Mb/up) compared to the cable connection I am used to, which was 10 Mb/down by 2 Mb/up.  

With 4G my speeds are  14.75 Mb/down by 4.75 Mb/up.  It's not a great solution for gaming because the latency is higher over 4G, but for everything else, it rocks.  The Verizon 4G LTE  signal also penetrates walls better and I find the connections to be more solid and reliable.

I would suggest that as soon as your area has 4G, go for it.

Hope this helps.

---

### Post by WindingRoad on 2012-02-26
Thank you very much.  We are supposed to get 4G this summer.  As I said before if I don't see a major improvement I'll pay the big bucks to get outta my contract with Verizon and go with GWI.  Unlimited access. I could watch movies all day.  LOL...

---

### Post by WindingRoad on 2012-03-05
Well, seems good things do always last.  This samsung thingy is doing the same thing all over. So I went to the Verizon site.  Seems they have a software up date.  For PC's only with windows.  Damn.  I suppose I gotta get out my old HP and fire it up.  LOL Now if I down load the new soft ware I'm guessing it will do something to this expensive hand warmer.  And then I'm supposing it will work with my MAC.  There was a firm ware up grade listed also. I didn't bother to look at that because I'm sure it's only for PC's running Windows.  YUCK.  But there was one thing I did.  Verizon said to un check  BROADCAST SSID   so I did.  And it seems to be working better.  Cross your fingers or save some money to bail me outta jail.. LOL

---

### Post by mosby1865 on 2012-04-26
Thanks for the info. Return the Windows/MAC box to the owner and say thank you.lol

---

### Post by gchokyong on 2012-11-20
:guitar:I know it's a little redundant at this point but THANK YOU. To say that I am new to linux would be a serious understatement, I can count the hours I've spent with it on my fingers...  and this sch-lc11 problem was the first one I ran into, it surprised me because it's the same kind of wacky behaviour that made me ragequit windows and install ubuntu in the first place lol. I just can't thank you enough, such a simple solution! ^_^

---

### Post by mgmiller on 2012-11-23
You're welcome.  I'm glad I could help.  :popcorn:

---

