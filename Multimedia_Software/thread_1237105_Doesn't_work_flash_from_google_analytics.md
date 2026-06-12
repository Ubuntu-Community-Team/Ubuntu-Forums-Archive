---
title: "Doesn't work flash from google analytics"
date: 2009-08-11
forum: Multimedia Software
---

### Post by linderox on 2009-08-11
I have the lastest version of flashplayer from medibuntu, the lastest version of Firefox and Epiphany from ubuntu, flash on the other sites works well, but on the google analytics I don't see graphs. The page loads, but on the place where graph situated there is usuall continious icon of loading, but it's infinite loading for me. 
There is no adblock , firewall and other such stuff

---

### Post by anilimb on 2009-08-13
I'm also facing the same problem when using Google Analytics with my Ubuntu machine. I have the latest version (9.04) of Ubuntu installed on my machine. Please help me to fix this problem

---

### Post by oxy86 on 2009-08-18
I had the same problem in a fresh Kubuntu 9.04 installation of a friend. 
He could nicely see any flash on Youtube etc, but no graphs were displayed in google analytics. We searched for a while, reinstalled flash, installed flash from adobe, with no luck. 

It turned out that he had clicked on "install flash plugin" notification inside Firefox, thinking that this would be enough like in Windows. After that, he installed flashplugin-nonfree from kpackagekit but apparently something was wrong already.

The solution? We reinstalled the same Kubuntu, but this time we installed flash plugin from command line:

sudo apt-get install flashplugin-nonfree

And that was enough. Now, my friend enjoys google analytics as usual.



[[IMG]http://tinyurl.com/qm6nhf[/IMG]]("http://www.supersyntages.gr")

---

### Post by textas on 2009-10-13
had the same problem; after reading the reply above, i didn't do a clean install - i just used Synaptic package installer to remove anything related to flash (mark for complete removal and then apply modifications) i then used terminal and apt-get:

sudo apt-get install flashplugin-nonfree

and it worked just fine: google analytics are now well displayed
hope this helps


note: there was a swf mozilla thing installed that might have caused some confusion - ?

---

### Post by Brother F on 2011-04-13
Thanks oxy86, 
I had the same problem, no flash graphs in Google analytics using both Chromium and Firefox.
I did the same thing as textas. It's now working perfectly.

Thanks!

---

