---
title: "Networking for remote area?"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by ericmachine on 2013-06-15
[COLOR=#000000][FONT=Arial]Hi everyone,

I know this may not be an exact ubuntu related questions. But I wonder anyone can share some ideas to get me to the right path.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I need to setup IT infra at a remote location. The internet here is really slow and quite unstable. Since this is a remote area, the internet service provider has very little coverage and it's really expensive here. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My scenario:-
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have 2 offices in this remote area. Both offices distances around 500 meters to 1 km away.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Office 1 &#8211; All my servers will be located here (all of them are ubuntu servers 12.04 LTS)
Office 2 &#8211; need to access office 1's servers. Need to setup LAN as I can't rely the internet here. But I can't pull LAN cables that far away and doesn't really make sense.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Note: Inside this office 2, I have 3 different blocks where I have LEDTVs as dashboard for work monitoring. This data will be pushed from Office 1 to be displayed on these LEDTVs. If I need to wire up LAN cables for these 3 blocks, will be tough too. But WIFI is really bad here. Is there any way I can boost WIFI strength or something?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HQ (outside of the remote area, basically my office) &#8211; since internet is an issue in office 1, I will get my Office 1's servers to perform daily batch updates at 2 a.m. to my HQ server.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Few questions:-
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]a. How can I achieve what I need above? Any better solutions maybe open source?
b. For batch updates, is 2 a.m. the right timing?
c. Any way to boost internet speed and reliability?
d. Is there any way I can boost wifi speed? Having cisco 2.4GHz and 5GHz can't help much here.
e. someone suggested me to use this rocket m [http://www.ubnt.com/airmax#rocketm](http://www.ubnt.com/airmax#rocketm) (point to point or point to multi locations) but i am not sure whether this is overkilled for me.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]How do you plan for your remote architecture?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]For better internet access, do people use vsat link?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Any help from this community? Thanks.[/FONT][/COLOR]

---

### Post by houstonbofh on 2013-06-15
You really have a lot of different questions here, and they are kind of mixed up.  So I will focus on two of them.

Yes, you can get a reasonably high bandwidth link between tow locations 500 meters away...  This requires good equipment.  I like the EnGenius hardware with high gain directional antennas.  I have had solid 50meg connections at just over 1 mile. (1.6 kilomoters)  This was also in clean air with line of sight, not downtown!  The newer APs can support up to 300 meg, so 200 is not out of line at that distance. [http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16342-ecb350](http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16342-ecb350) or [http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16757-ecb600-coming-soon](http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16757-ecb600-coming-soon)  Also, you could have 3 links with LACP if you have supporting routers for about 1 gig of full throughput.

As for access in the hinterland, you are limited to what is available.  Yes, you can go satellite, but the latency is so bad that it seems very slow.  You may be better off finding a place with fiber within a kilometer or so...

---

### Post by ericmachine on 2013-06-15
> **houstonbofh said:**
> You really have a lot of different questions here, and they are kind of mixed up.  So I will focus on two of them.

Yes, you can get a reasonably high bandwidth link between tow locations 500 meters away...  This requires good equipment.  I like the EnGenius hardware with high gain directional antennas.  I have had solid 50meg connections at just over 1 mile. (1.6 kilomoters)  This was also in clean air with line of sight, not downtown!  The newer APs can support up to 300 meg, so 200 is not out of line at that distance. [http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16342-ecb350](http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16342-ecb350) or [http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16757-ecb600-coming-soon](http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16757-ecb600-coming-soon)  Also, you could have 3 links with LACP if you have supporting routers for about 1 gig of full throughput.

As for access in the hinterland, you are limited to what is available.  Yes, you can go satellite, but the latency is so bad that it seems very slow.  You may be better off finding a place with fiber within a kilometer or so...

Thanks for replying back.

Few questions.

a. Shouldn't I get the outdoor device? Both of your proposed models are more to indoor purpose?

Something like this [http://www.engeniustech.com/business-networking/outdoor-access-points-client-bridges/16334-enh210ext](http://www.engeniustech.com/business-networking/outdoor-access-points-client-bridges/16334-enh210ext)

But I can't seem to find the distances which the devices can support? 

I need to setup this in Newman, Western Australia. It's really hot here especially summer (as high as 45 - 50 degree celcius), not sure the signal will be affected.

b. So engenius product is better than ubiquiti?

c. Some said I can consider nanobridge. How does nanobridge differs with engenius solution?

d. for fiber, it's gonna costs a bomb. Everything is expensive in here.

Any help? Thanks.

---

### Post by 18echo on 2013-06-15
The ENH210EXT supports 300Mbps at distances of up to 4 miles, the specs state that there is a 14dbi internal antenna in the housing.

---

### Post by houstonbofh on 2013-06-15
I was thinking of having the AP indoors, and olny the antenna outside.  Makes keeping it cool easier.

As far as heat goes, yes, it does effect transmissions somewhat.  But moisture does more.  Rain over a mile is harsh...  The point is to throw more power, and use it more efficiently (hi-gain antennas) at the troubles.

And I have probably installed hundreds of EnGenius APs, and I still like them.  Nothing has the power they do.  I have even used them in enviorments that Cisco with a high end controller could not handle.

---

### Post by ericmachine on 2013-06-16
> **houstonbofh said:**
> I was thinking of having the AP indoors, and olny the antenna outside.  Makes keeping it cool easier.

As far as heat goes, yes, it does effect transmissions somewhat.  But moisture does more.  Rain over a mile is harsh...  The point is to throw more power, and use it more efficiently (hi-gain antennas) at the troubles.

And I have probably installed hundreds of EnGenius APs, and I still like them.  Nothing has the power they do.  I have even used them in enviorments that Cisco with a high end controller could not handle.

Thanks everyone for replying back.

a. When you say having AP indoor and only the antenna outside... say I use this one 

[http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16342-ecb350](http://www.engeniustech.com/business-networking/indoor-access-points-client-bridges/16342-ecb350)

So how can I have the antenna outside? Do I need to buy extra accessories for antenna?

b. when you say install hundreds of engenius APs, why so many? to prevent the heat issue? 

i assume if there's rain, signal will be bad too?

c. lastly, is this engenius easy to setup? I hope I can do this manually myself.

---

### Post by kurt18947 on 2013-06-16
Is this line of sight? A highly directional antenna seems like an option.  If you're a reasonably skilled tinkerer, do you know about Cantenna?  Googling "cantenna" brings up several likely sources of information

[http://en.wikipedia.org/wiki/Cantenna](http://en.wikipedia.org/wiki/Cantenna)


Here is a link where I first heard about the idea.  This guy was extending a WiFi signal several kilometers, I believe.  He got 2 or more months' worth of columns from his experiment.

[http://www.pbs.org/cringely/pulpit/2001/pulpit_20010628_000421.html](http://www.pbs.org/cringely/pulpit/2001/pulpit_20010628_000421.html)
[URL="http://en.wikipedia.org/wiki/Cantenna"]

[/URL]

---

### Post by houstonbofh on 2013-06-16
You would need to buy, build, or somehow acquire a high gain external antenna in the 2.5 and / or 5 ghz range.  Like this one for 2.4ghz. [http://www.caworldwifi.com/24db-gain-parabolic-wifi-grid-antenna.html](http://www.caworldwifi.com/24db-gain-parabolic-wifi-grid-antenna.html)  A short article on that is here. [http://www.squidoo.com/are-super-long-range-wifi-antennas-legal-](http://www.squidoo.com/are-super-long-range-wifi-antennas-legal-)

Then, you just run the cable out the window, or though a wall vent.

As to why...  For several years I installed WiFi in hotels, bars, and marinas.  I actually got to know some of the engineers a bit, as I found a lot of issues they missed in QA. :)

---

### Post by chili555 on 2013-06-16
I wonder if this may be helpful: [http://www.wispequipment.com/customer-premises-equipment-cpe/](http://www.wispequipment.com/customer-premises-equipment-cpe/)

---

### Post by ericmachine on 2013-06-17
> **houstonbofh said:**
> You would need to buy, build, or somehow acquire a high gain external antenna in the 2.5 and / or 5 ghz range.  Like this one for 2.4ghz. [http://www.caworldwifi.com/24db-gain-parabolic-wifi-grid-antenna.html](http://www.caworldwifi.com/24db-gain-parabolic-wifi-grid-antenna.html)  A short article on that is here. [http://www.squidoo.com/are-super-long-range-wifi-antennas-legal-](http://www.squidoo.com/are-super-long-range-wifi-antennas-legal-)

Then, you just run the cable out the window, or though a wall vent.

As to why...  For several years I installed WiFi in hotels, bars, and marinas.  I actually got to know some of the engineers a bit, as I found a lot of issues they missed in QA. :)

Thanks for sharing.

But if I setup 1 or 2 nanobridge M from ubiquiti, the price doesn't seem to be that far away compare to setting up netgenius + external antennas.

If price budget is not an issue, going with nanobridge will be better?

If I set up nanobridge or the engenius ones, say in between 2 offices there are tall trees and tall buildings ... will that affect the wifi signal? Do I have to make it tall enough?

Will wifi signal get affected if the area is dusty? Newman is really dusty place.

Any help? Thanks.

---

