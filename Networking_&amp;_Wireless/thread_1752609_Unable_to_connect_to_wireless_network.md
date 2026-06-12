---
title: "Unable to connect to wireless network"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by Hemdawg on 2011-05-08
Hi all,

I've just tried to connect to a wireless network, using a Belkin Wireless N dongle, for my computer running Ubuntu 10.04, Kernel 2.6.32-31-generic, gnome 2.30.2

The computer is running dual boot with Windows, which is connecting to the network fine, so I have to assume its something to do with the computer set up, or some shennanigans. I'm not the most familiar with Ubuntu, so I dont know where best to start - but thats what the community is for, right? :)

So - a number of networks are showing up in my wireless networks list, but not the network I want to connect to.

Can anyone provide any help with what I need to do from here.
Thanks

---

### Post by horusr on 2011-05-08
So ; let me see if i understood you; You can see other networks which means the card is working,right?.. otherwise you  wouldnt even see them ,?.. right?.. OK next : DO you know for certain that the network is sending ,broadcasting , or that it's even turned on?.. It might be set not to ,in which case you would need to KNOW it's Name SSID and it's Passmode ; wep /wpa ...etc  and if you don't there's some great softwr that will help you connect to anything ... even a satellite, & NO i am NOT kidding ...
  Now that we met, How long ago did you post this thread ?.. Sorry i was still sleeping ;it's Sunday morning 
... and i think someone spiked my beer last night , can you --help me 1 fax me a lt of Milk ... moo moo...

---

### Post by Hemdawg on 2011-05-08
Yep - the dongle looks like its working, cos its seeing other networks.
Yep - the network is broadcasting, because thats what I'm posting this from (different machine)

I do know the SSID and passmode, because I have them on this machine - do I need to try connecting to a hidden network or something?

I was going to try a different network manager, but I cant download anything on the machine, because its not connected to the net :S

Any thoughts on the next steps?

---

### Post by MDBill on 2011-05-08
If you don't see your WiFi node on the list then it's almost certainly not broadcasting its SSID. In which case, you should select the "Connect to a Hidden Wireless Network..." option and supply the correct node name and passphrase.

---

