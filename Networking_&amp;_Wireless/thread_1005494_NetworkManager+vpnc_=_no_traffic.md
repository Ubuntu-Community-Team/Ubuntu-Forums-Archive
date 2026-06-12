---
title: "NetworkManager+vpnc = no traffic"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by defcon3 on 2008-12-08
Hello folks! 

For quite some time I had given up on the idea that NetworkManager will work with VPN.. Well, a new release came along and my dreams got a new push... All things run smooth and I do manage to connect to my office VPN, have the fancy lock on top of the network bars, etc... BUT! I have no traffic whatsoever.

Thinking I am to blame (as in 99,9% of cases) I downloaded and installed Fedora 10 on a separate partition of the SAME laptop. Imagine my surprise when, once I put in the settings, user, pass it not only worked but it worked flawlessly! 

Naturally, I wrote down one by one all settings from Fedora10 and "pasted" them into Ubuntu 8.10 to make it work. I compared the "route -n" results: 
the only difference is that in Ubuntu, the iface is called ath0 while in Fedora it is wlan0 ;)

Whatever I tried, I failed - could someone please give me a hand - both distros have NetworkManager 0.7.0, both have the vpnc plugin installed, both have *identical* settings but for some weird reason Fedora works flawlessly, while Ubuntu has *no traffic*, I cannot even ping my VPN address... 

Thanks!

---

### Post by defcon3 on 2008-12-19
Ok, for quite a while I got no feedback, so I've been beating it with a stick to see how far I get :) 

Basically, I have narrowed it down to the Atheros drivers - as soon as I plugin a cable from the same router which broadcasts the wireless, VPNC works like a charm; not so with the wireless. This is why I think it all boils down to drivers. Anyone agree with my theory? I am no expert, so I'd appreciate any feedback ;)

Happy holidays everyone :popcorn:

---

### Post by tpurch on 2009-01-16
> **defcon3 said:**
> Ok, for quite a while I got no feedback, so I've been beating it with a stick to see how far I get :) 

Basically, I have narrowed it down to the Atheros drivers - as soon as I plugin a cable from the same router which broadcasts the wireless, VPNC works like a charm; not so with the wireless. This is why I think it all boils down to drivers. Anyone agree with my theory? I am no expert, so I'd appreciate any feedback ;)

Happy holidays everyone :popcorn:

yes, i guess its possible.....if i understand your problem correctly no vpn traffic in ubuntu via wireless, but if you run Fedora10 it works with wireless and is configured the same with the exception of device name......

can you comparing the output of ifconfig -a before and after connecting and post along with routing tables? also, you say it works with ubuntu with wired connection.....can you compare both routing tables for them and post the results.

---

### Post by tate on 2009-01-16
this is very strange.  i'm having the same issues and i've posted in another topic where someone is having similar issues.  i tried connecting via wired connection and it still doesn't work.  i can resolve host names, ping boxes that are on the vpn network, but i can't connect to any servers via ssh.  the connection to the server locks up at the "Last login..." screen output.  sometimes i'm able to get all the way in, and list a directory, but then i list another directory and it locks up.

as i said in the previous thread, this usually is a sign of the MTU being mismatched and packets being dropped, but this isn't the case.

not sure where to go on this one.  i've built a windows-based virtual machine and it connects fine.  going to test an opensuse11 virtual machine this evening.  i'll report back.

---

