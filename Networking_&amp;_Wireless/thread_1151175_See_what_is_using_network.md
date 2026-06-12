---
title: "See what is using network?"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by shane2peru on 2009-05-06
I have the little applet on the panel that monitors processor, memory, network etc.  Sometimes it is showing some network stuff going on and I want to find what application is accessing the web.  I know there must be some simple little app (cli or gui) that does this.  Can anyone recommend one that shows what app is accessing the web?  Thanks!

Shane

---

### Post by dacorr on 2009-05-06
from terminal type netstat

should list all connections and ports being listened on but may not have a connection.

Dac

---

### Post by shane2peru on 2009-05-06
> **dacorr said:**
> from terminal type netstat

should list all connections and ports being listened on but may not have a connection.

Dac
Wow, that does satisfy simple!  It is a bit overkill though.  I just want to know what applications are accessing the web.  This goes into extreme detail about network connections.  Anything a little less detailed?

Shane

---

### Post by shane2peru on 2009-05-08
Wow, I really thought this was a simple one.  I guess not.  I want something similar to top.  I found atop but when I press 'n'  it says something about a kernel patch not being installed or something.  That really looks close to what I would want, especially by pressing 'n' and seeing what apps are accessing the web.  Any other thoughts would be greatly appreciated.  

Shane

---

### Post by groovomata on 2009-05-08
Etherape is a good option. It does a neat graphical display of the network traffic on your computer.

---

### Post by superprash2003 on 2009-05-09
+1 etherape

---

### Post by eentonig on 2009-05-09
iptstate might give you the info you want. But you must install it first

---

### Post by Gnea on 2009-05-09
I'm going to recommend etherape as well, you can pretty much figure out how much bandwidth an application is using by monitoring it in realtime and matching the color-coded index.

---

### Post by shane2peru on 2009-05-09
ok, thanks for the info!  I have installed etherape, and it gives me this error: 
Error getting device, no suitable device found.

That is odd, I looked in the preferences but didn't see anything. I'm sure it is just a setup option or something to point it to my ethernet card.  Where do I set that?  Thanks.

Shane

Oops, a quick google tells me to run it as root. :)  Checking it out.  Thanks.

Ok, etherape is cool, but I don't see what apps are accessing the web, is there a way to do that?

---

### Post by groovomata on 2009-05-09
Did you launch 'Etherape (as root)'? It should be in the main menu in the Internet section. Mine has 'Etherape' and another 'Etherape (as root)'. Launch the 'Etherape (as root)'. It will ask for you sudo password.

---

### Post by groovomata on 2009-05-09
Hmm, I'm not sure. Under the 'Capture' item in the menu, you can play around with the 'Mode' between Ethernet, IP and TCP. I guess I infer what is what by the address that is showing. I suppose you can use it in conjunction with Network Tools in the Administration menu, especially the Netstate Tab, and select 'Active Network Services' and hit the 'Netstate' button.
It's not elegant but it's something.
Erik.

---

### Post by shane2peru on 2009-05-09
> **eentonig said:**
> iptstate might give you the info you want. But you must install it first

ok, installed it, how does it work?  Can it show the apps that are accessing the web?  

Shane

---

