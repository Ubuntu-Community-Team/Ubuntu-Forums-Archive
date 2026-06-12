---
title: "Wireless Periodical Lag"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by thelawenforcer on 2010-02-12
If anyone is familiar with windows, you would have to shutdown a service called 'Wireless Zero configuration' in order to stop the wireless sniffing around trying to find a better network. This sniffing would cause a big burst of lag every 30 secs or minute.

Ive recently installed ubuntu (today) and its rather nice, a bit of a learning experience but im going to give it a shot. 

However, apart for all the good stuff, ive noticed this little issue with the wireless. It seems to lag every minute or so. Now, im not sure its this sniffing around, but i suspect it is, and was wondering if there was a way to switch it off.

Keep in mind that im a linux noob, so try to keep terminal action down to a minimum(id like to work my way up to being able to use it confidently, but its quite different to the stuff im used to, even tho i have some dos experience from years and years ago :P)

Thanks for your help!

---

### Post by thelawenforcer on 2010-02-15
Bump.

Thought id give some specs. 

Its Ubuntu 9.10 and im using a Belkin Usb Wireless adapter Model : F5D9050

Surely there must be a way to keep it locked on one wireless source and stop it looking around for alternatives (which is what i suspect is the cause of the lagging)

---

### Post by thelawenforcer on 2010-02-15
noone? im seriously considering going back to windows as a smooth internet connection is critical for me.

---

### Post by Pltinum on 2010-04-22
Nobody? Same problem here.. :(

---

### Post by aport on 2010-04-22
I have the same issue. I've tested with two different wireless routers and two different wireless adapters.

I've tried switching channels, different encryption types, everything... Then I noticed that I didn't have a problem on my Windows box. So, it's definitely a linux or Ubuntu problem. I haven't tested other distros... though I might.

This problem is very annoying!

---

### Post by Pltinum on 2010-04-23
Assuming it was NetworkManager trying to look for better connections, I tried switching to wicd, only the problem is even worse, it doesnt give a lag spike every minute or so, but every 3 seconds.

I tried wicd, because they suggested turning of NetworkManager and connect via command-line. And I just don't know how to do it. (even just killall NetworkManager doesnt really work, because it just reopens itself). I've installed madwifi as well with no luck.

edit: The problem seems pretty much fixed now after installing wicd. Well not really fixed, just a solution. Although sometimes a bit laggy, It's not a sudden 2sec BURST of insane lag. But just here and there, which I assume is because we're using a "normal" internet account for 11 people.

---

