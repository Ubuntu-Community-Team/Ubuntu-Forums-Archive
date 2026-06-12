---
title: "Complete n00b needs help w/ wireless - Linksys adapter"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by Aspirin on 2005-12-21
I'm sure this is a common question, but how would I go about installing my wireless card (a Linksys WUSB54G usb adapter)? Here's what I've done so far....

Using the Synaptic Package Manager I installed ndiswrapper.
I've copied the WUSB20XP.sys file and the WUSB54G.inf file to my desktop.
I've plugged in the adapter.

So where do I go from here? I have the files I need, but I have no idea what to do with them. Please, if you could explain this to me in english, that'd be great....I'm not used to working with the Terminal. I need step-by-step instructions. 

Thank you very much in advance!!

---

### Post by gnu2tux on 2005-12-21
which version of the usb adapter are you using (1 or 4), it usually says on a sticker - from what I have read about your adapter, only one version works under linux - just from a quick google.

Before you start, do this at the command prompt:

ifconfig

and copy and paste the output back to this post.

I have never used ndiswrapper as I have an ethernet based setup (which is much better than cheapo-usb ones btw), but I believe you tell ndiswrapper where your inf file is like so (make sure you are in the directory where the .inf file is):

sudo ndiswrapper -i WUSB54G.inf
sudo modprobe ndiswrapper

see my tutorial for help with the command line ([http://www.linuxnewbieguide.org/chap12.php]("http://www.linuxnewbieguide.org/chap12.php"))

once you have done that do ifconfig again, and paste that back as well. If there is now an interface there, it will probably indicate that the driver has installed successfully.

for more info on ndiswrapper, go to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")


Hope this helps!

---

### Post by Aspirin on 2005-12-21
i'm gonna try a few more things and see if they work....i'll get back to you soon. if i dont have it working by tomorrow, i'll be back for help. thanks for the advice tho!!

---

