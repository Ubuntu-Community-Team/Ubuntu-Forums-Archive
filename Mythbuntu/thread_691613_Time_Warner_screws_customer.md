---
title: "Time Warner screws customer"
date: 2008-02-08
forum: Mythbuntu
---

### Post by volkswagner on 2008-02-08
I have been trying to get firewire working on my Samsung SMT-H3050, HD set top box from Time Warner, Hudson Valley, NY

After unsuccessful attempts with firewire tester, I decided to call Time Warner to get the 1394 port enabled.  I was told this was not enabled on this device nor will it be.  I was told I need to get their PVR box to get an enabled 1394 port.  Have they created a loophole to the 2004 FCC mandate to provide me with a functional port.  I believe this would be an added ten bucks per month, WTF!

---

### Post by LorenzoS on 2008-02-11
That sucks, I am a TWC customer in Northern NJ and was planning to use the Firewire port also.  I wonder if anyone has had success getting this?

---

### Post by theacoustician on 2008-02-11
I don't believe that they can do that.  However, in order to get what you're after, you're going to have to dig up the FCC memo that outlines firewire provisioning in STBs, read it thoroughly, and then call back and ask for a manager.  I'm sure its not as much they're trying to screw you as it is you reached some call center flunky that doesn't really know anything.  Good luck.

---

### Post by volkswagner on 2008-02-11
I have the information from the FCC, which they emailed me after calling them.  I was not very happy with one statement made by the FCC agent.  He said "Well I am not sure if they have and exemption in your area, and it seems they are trying to provide you with a functioning port".  

Now it seems we are interpreting law and the following line.

> 
(4) Cable operators shall:

(i) Effective April 1, 2004, upon request of a customer, replace any leased high definition set-top box, which does not include a functional IEEE 1394 interface, with one that includes a functional IEEE 1394 interface or upgrade the customer's set-top box by download or other means to ensure that the IEEE 1394 interface is functional.

The above is an excerpt from 

> The rule is 76.640 and available online from a link at wireless.fcc.gov/rules.html

So do I need to put my LAWYER hat on?

I called Time Warner this morning and asked to speak with a manager.  I was told he will call me back.  I am still waiting for said call.  I also asked TW if I could get the DVR box with the firewire enabled and DVR disabled to avoid the Ten bucks a month.  They said that it was not an option.

Seems odd this rule was written prior to year 2000 and implemented in 2004 yet I still have to pull teeth.

---

### Post by theacoustician on 2008-02-12
> **volkswagner said:**
> 
Seems odd this rule was written prior to year 2000 and implemented in 2004 yet I still have to pull teeth.You have to understand that most people don't even know about this ruling and even fewer fight their cable companies to get it enforced.

I'm not sure if this will help you or not, but let me give you some insight into their state of mind.  Honestly, TW couldn't give two craps about what you do with your cable once its inside your house for the most part.  What they are looking at is licensing fees.  TW has to buy the cable box from the manufacturer (probably Sci. Atlanta or Motorola), then license firmware and middleware to run them.  These pieces of software are priced per feature enabled.  For instance, HD is usually an extra charge as is PVR.  Same thing for enabling firewire output.  They aren't allowed to license for a single box.  If someone screwed up and didn't license firewire on your series set top box, then they'd have to buy it for all the boxes they have of that series which could add up to 10's or even 100's of thousands of dollars.  So what should you do?

1. Don't tell them what you want the firewire for.  Its none of their business and they'll only use your reason to try and turn it around and sell you one of their products.  Just say you have a specific need for firewire and leave it at that.

2. Quote the FCC rule verbatum.  Start every sentence with "I'm quoting FCC rule 76.640 section 4.i and it says ...".

3. Understand the manager's limitations.  He can't change the licensing on the box you have without breaking contracts with their hardware or middleware providers.  What they can do is give you a box that works the way you want for zero upcharge.

4. Be positive and polite.  Start out with things like "I have this issue and I know you're the person who can sort it out for me" and keep up with that.  Always make it sound like your will is what the other person wants to do and express your belief in their ability to accomplish it for you.

Good luck man.  I hope that helps some.

---

### Post by volkswagner on 2008-02-13
I did not receive the phone call from any manager.

I decided to call again.  After speaking to two representatives I was finally connected to a lovely lady who knew a thing or two.  Thanks Amanda where ever you are.

I was told I could get the SA-3250.  See link below.  Why couldn't I find this.  Please let me know what y'all think about how crippled this will be.  From my newbie eyes it seems to be just what I have expected from my research.  I am assuming the limitations listed such as program guide will not be available....This will only be unavailable while output to 1394, not if I am viewing via normal TV out, such as composite.

[http://www.timewarnercable.com/nc/products/cable/firewire.html]("http://www.timewarnercable.com/nc/products/cable/firewire.html")

---

### Post by theacoustician on 2008-02-13
> **volkswagner said:**
> I did not receive the phone call from any manager.

I decided to call again.  After speaking to two representatives I was finally connected to a lovely lady who knew a thing or two.  Thanks Amanda where ever you are.

I was told I could get the SA-3250.  See link below.  Why couldn't I find this.  Please let me know what y'all think about how crippled this will be.  From my newbie eyes it seems to be just what I have expected from my research.  I am assuming the limitations listed such as program guide will not be available....This will only be unavailable while output to 1394, not if I am viewing via normal TV out, such as composite.

[http://www.timewarnercable.com/nc/products/cable/firewire.html]("http://www.timewarnercable.com/nc/products/cable/firewire.html")
Sounds fair and I think you'll get about what you expect.  All digital basic tier channels.  Obviously premium channels and analog won't show, but hopefully you knew that.  If you use Myth's EPG with SchedulesDirect, do you need the TW EPG ever?

I'm not sure about this one, but perhaps you can trick Myth into controlling the box as a typical STB for live viewing (IR control + input switching on the TV) and using the firewire interface as a capture device and having Myth switch back to the PC input on TV for all other occasions.  Make sense?  Seems like that should be doable after a fashion, but I've never attempted such a thing.

---

### Post by ickyb0d on 2008-02-19
> **volkswagner said:**
> I was told I could get the SA-3250.  See link below.  Why couldn't I find this.  Please let me know what y'all think about how crippled this will be.  From my newbie eyes it seems to be just what I have expected from my research.  I am assuming the limitations listed such as program guide will not be available....This will only be unavailable while output to 1394, not if I am viewing via normal TV out, such as composite.

[http://www.timewarnercable.com/nc/products/cable/firewire.html]("http://www.timewarnercable.com/nc/products/cable/firewire.html")

This is exactly what I have from TW in southeastern wisconsin.  As of now, I'm only able to stream "free" channels (ones that are already broadcast over the air), and that's about it.  The other digital channels are (5c?) encrypted, and you can't establish a p2p or broadcast connection when the box is tuned to one of them.

Initially I was hoping i could at least use the firewire to change channels, and use one of the other outputs on the box, but have yet to be successful in getting that.

---

### Post by majoridiot on 2008-02-26
good luck on this.  i fought my provider (insight, now comcast) for incorrectly applying copy-protection
on channels that are mandated by law to be open.  i gave up after a year of getting nowhere on every level
of both the cable company and the FCC.

sadly, you will find that you will find no joy with the FCC... and if you do go to the trouble of educating 
yourself on the statutes, you will wind up talking with a bureaucrat at the FCC that neither knows, 
nor particularly cares about, firewire statutes.

cable companies have been running roughshod over the consumers for years when it comes to firewire...
and the only thing that will change it is the phasing out of 1394 ports altogether.

---

### Post by pastafazoule on 2008-04-23
why is it when i dont have the firewire hooked up to the mac it says disabled,then when i hook it up it will say univalable,is it because tw is blocking my connection to the mac or is it a software problem that should be updated,this is with the 8300 box with tw

---

### Post by majoridiot on 2008-04-23
> **pastafazoule said:**
> why is it when i dont have the firewire hooked up to the mac it says disabled,then when i hook it up it will say univalable,is it because tw is blocking my connection to the mac or is it a software problem that should be updated,this is with the 8300 box with tw

that's a question for TWC... although it makes sense if the firewire port is disabled or only conditionally enabled.

to me, "disabled" says that it is not enabled in firmware, so the status changes to "unavailable" when the stb sees a
firewire connection has been made, but does not have the ability to use it.

you may find more information on how to get more useful info from the stb here: [http://www.digitalhome.ca/forum/showthread.php?t=17719](http://www.digitalhome.ca/forum/showthread.php?t=17719)

in any event, TWC is mandated by law to enable the firewire port if one exists- so push that issue.  whether or not there
will be many unencrypted channels once they do, is yet to be seen.

good luck! :)

---

