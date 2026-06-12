---
title: "Advanced Network Setup - Second Opinions please,,,"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by JackRabid on 2011-04-29
I have a project that I would like to provide hosting for, and over the last few months have been working toward that goal. I have a couple servers that I installed Ubuntu Server on and have been using those to learn on. And things have been going pretty well with that. So well in fact, now that I feel a bit more comfortable with working from a command line again, I would like to be able to do a 'final' setup of the network side so that I can return my attention to my project for a bit.

My setup: Client -> Internet -> No-IP.org redirect -> Internet -> Cable Modem -> Router -> ... ... ... the rest is better explained by the picture.

[IMG]http://www.phnxkicksass.org/two/webimages/forums/ubuntu/networkproposals.png[/IMG]

I was trying to keep the image somewhat compact and as such didn't put in the 'Client -> No-IP..." stuff. Some additional machines are shown just to add flavor and to show why some things need to be routed the way they are. But as you can see- the only real question is what would be the best method to relate the Web Server and App Server to the internet, and to each other? And how does this relate to the No-IP redirect?

Should I just slap a static IP on everything- open and forward my needed ports as in Example A? Add a second NIC to the Web Server and place the App server behind the web server as in Example B? Or place that whole side of the setup out in the DMZ provided by my SOHO router as in Example C? Some combination of my supplied examples? Some variation that I have yet to consider?

To be honest I would like my servers to have some level of protection and am, perhaps foolishly, reluctant to put the servers out in front of the router in the DMZ... I'm not sure how the 2 servers from the same IP tie into it from the no-IP side. Will I need to run my own DNS server... Will I need to run DNS on both servers?

Sorry for the flood of questions, I kinda started thinking through my fingers at the end there a bit. ;)

---

### Post by JackRabid on 2011-04-30
Nothing...? No one...?

Is my question that bad?

---

