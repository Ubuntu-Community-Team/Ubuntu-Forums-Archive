---
title: "Setting up Tor as system wide proxy"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by faillord adam on 2012-06-23
Is it possible to set all network activity to go through Tor?

Not doing anything illegal, but I'd rather not have the UK government looking at everything I do.

---

### Post by hakermania on 2012-06-23
> **faillord adam said:**
> Is it possible to set all network activity to go through Tor?

Maybe, but if you want this kind of anonymity, then you should probably check out the [Tails ISO]("https://tails.boum.org/") :)

---

### Post by linuxnutjob on 2012-08-04
it is possible as i have done it.  Here is how you do it:
Menu>System>Preferences>Network Proxy
check the 'manual' radio button
in the 'socks host' insert '127.0.0.1' then...
here is where the problem occurs...when you close and reopen TOR, it auto assigns a new port...so every time you close and reopen TOR or restart your computer you will have to manually input the port.
open your tor browser (firefox) goto edit>prefernces>advanced>network>connection, click settings...note the port number.
Go back to your ubuntu network proxy and enter that port number in the port box next to 'socks host'
since you dont want to make this your default go to the top of the window where it says 'location' and create a new location like "TOR" then 'ok'
Once you've done all this, click 'apply system wide' enter your password whenever it asks...close the proxy window and restart your browser. DONE.  to test..in the URL address type 'check.torproject.org'..hit enter..you should get a positive affirmation of configuration.
Remember, every time you restart your computer or TOR, you will have to update the port number.
Here is a video on how to do this if it still seems difficult:
[http://youtu.be/7vxq6UB2LLU](http://youtu.be/7vxq6UB2LLU)
:popcorn:

---

