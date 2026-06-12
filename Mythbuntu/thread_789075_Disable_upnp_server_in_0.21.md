---
title: "Disable upnp server in 0.21"
date: 2008-05-10
forum: Mythbuntu
---

### Post by NarsilAnduril on 2008-05-10
Hi,

I have a 8.04 Mythbuntu fresh install and would like to disable the upnp server.

I know about the mythbackend --noupnp option, but not how to add this option to default start. How could I do that ?

Thanks for your help.

Diego

---

### Post by ian dobson on 2008-05-10
Hi,

You could try editing the /etc/default/mythtv-backend file and change the line #ARGS="" to read
EXTRA_ARGS="--noupnp" 

I've never tried it myself but it should work.

Regards
Ian Dobson

edit: Just tested it myself and EXTRA_ARGS does it for me.

---

### Post by NarsilAnduril on 2008-05-11
That's it !

Thanks Ian.

EXTRA_ARGS="--verbose --noupnp"

Diego

[edit] don't forget to uncomment (remove the #) in front of the row

---

### Post by electrogulp on 2009-05-21
well thread is very old but...  I hope in your help!
Is it possible that disabling UPnP became impossible to see tv on frontend?
Just a bit after disabled UPnP infact, starting frontend an error message occour that sound like "control ip address because there's no backend"
Help

---

### Post by ian dobson on 2009-05-22
Hi,

No disabling upnp just disables the second network communication method that mythbackend supports. UPNP is not used by mythfrontend to communicate with the backend.

Looks like you have a different problem. First check the IP address configured in the frontend against the IP address of the backend. Check that you can ping the backend from the frontend and check the backend logs under /var/log/mythbackend.log

Regards
Ian Dobson

---

