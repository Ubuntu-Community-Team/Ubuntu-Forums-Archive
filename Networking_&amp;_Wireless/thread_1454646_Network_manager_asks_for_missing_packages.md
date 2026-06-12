---
title: "Network manager asks for missing packages"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by hancoma on 2010-04-14
Network Manager 0.8 missing packages. 
Super new Ubuntu user (3 days!) I can usually figure things out, but not in this case:
When ./configure network manager, it runs for awhile, then stops stating it is missing a specific package...I find the package, and configure again...making it further down...until it stops and finds another package I am missing....I have been doing this for 3 days...and am very frustrated. 

Is there not a command that when network manager is installing it will automatically go out and retrieve the files it needs?

Not wanting to go back to my locked down mac, or always crashing windows...give me a reason to go on! :lolflag:

---

### Post by 2hot6ft2 on 2010-04-15
When you install things from the repos. they come with everything they need but it doesn't look like you did that.

Network Manager 0.8 is not in 9.10, if you found, and made it and installed it then go back where you got it and find the packages that it depends on that you're missing.
It's called dependency hell for a reason. That's why we have repos. which take care of those things so we don't have to go thru that.
You may be able to go to
System > Administration > Synaptic Package Manager
and search for network-manager-gnome
select it and click on Packagaes then Lock version and select the version that came with 9.10 from the drop down and click on Lock version then on Apply.
That is if 9.10 is what you're using since you never said.

And welcome to the forum. Things will work better once you learn how to do them right.

---

