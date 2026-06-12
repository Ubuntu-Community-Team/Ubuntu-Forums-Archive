---
title: "AT&amp;T Internet?"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by prayersfor.rain on 2011-04-18
Hi all,
I just moved and it's time to get my own internet account. I'm not sure who to go with. I was using comcast but it costs too much, and the prices go higher after 6 months. AT&T has a good price and it lasts for 12 months. There really aren't many other ISPs in town and they cost more as well.
 
Now I obviously know Comcast internet works with my computer, running Ubuntu, Maverick. I'm not sure about AT&T. On their website it costs a lot to have a technician come out and set it all up for you. So I looked into setting it up myself, and the website says stuff like if you have linux you can't do it yourself. I googled and everything I'm finding says that the AT&T technicians/customer service tend to say that their service won't work with Linux mostly because they don't know how to do it so if I run into any snags there won't be any help there. And I'm not finding any how-to's. I'm not a pro or anything, I can get around command line if I cut and paste, and I can do some very basic things. GUI is easier for me. I don't really have experience setting up internet/networking. 
 
So my plans are to self-set up if possible. Does anyone have any experience in this? I know there's a cd they give you and to set up you have to run their program (on Win or Mac) to do it which is why they say it won't work. Would I be able to use Wine to run whatever program this is? Or is there another way of just bypassing all of that?
 
Or would it just be easier to go with something I know that works, but costs more? :(
I don't want to call AT&T or any other ISP until I know for sure. I'm worried that I'll pay and they'll send everything out, and then it'll be incompatible and maybe I won't get my money back and I can't afford that right now.
 
I hope this isn't too hard. My wireless dongle is already plugged in and it picks up 3 locked networks in the area already so I think it's just this registration program I might have issues with.
 
Thanks for reading all of this, I know I tend to be wordy. Hopefully someone has experience or any advice! If you respond, it might take me a bit to get back to ya as I only have access to the web at work and I don't always have a chance to check back right away.

---

### Post by chili555 on 2011-04-18
I am answering from my Ubuntu computer connected to AT&T right now. I can't speak to all the various devices they use, but if you are being provided the common 2wire wireless-capable DSL modem, it is quite easy to set up in Linux and particularly Ubuntu.

I temporarily connected an ethernet cable and opened Firefox and navigated to [http://192.168.1.254](http://192.168.1.254). I set the DSL modem to do the user name and password authentication. I also changed the default 64-bit WEP encryption to WPA2 and selected a strong password not easily guessable; that is, not my house number or birthday. I also changed the password to authenticate changes to the modems configuration. I saved my changes and then disconnected the ethernet cable.

I returned to my usual chair and Network Manager saw my network and connected.

I think AT&T has some more sophisticated devices that require Windows. The more common 2wires are easily set up with Ubuntu.

---

