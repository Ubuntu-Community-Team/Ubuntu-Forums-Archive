---
title: "[SOLVED] Rhythmbox proxy problems - workaround"
date: 2008-07-23
forum: Multimedia Software
---

### Post by beow on 2008-07-23
It seems like rhythmbox does not honor the settings of the System->Preferences-Network Proxy settings, at least not for mms streams, which is needed in order to listen to internet radio systems behind a firewall/proxy. There are some workarounds for this problem.

1. (Not recommended) To insert the lines

```
http_proxy=http://<proxy-address>:<proxy-port>/
export http_proxy
```

in ~/.gnomerc. In this way the environment variable http_proxy is exported to all gnome applications and rhythmbox the works with the proxy. However, I think that this would interfer with "Network Proxy" setting in the System meny, which is not a good thing.

2. (Recommended). Add

```
http_proxy=http://<proxy-address>:<proxy-port>/
export http_proxy
```

to your ~/.bashrc file (create if necessary). Then open a new Terminal and start rhythmbox:

```
$ rhythmbox &

```
Now it should be possible to listen to internet radio. However mms:// urls are not resolved correctly and need to be converted to mmsh:// urls. I did this by going to the :~/.gnome2/rhythmbox directory and ran:

```
$ sed -i -e 's/mms:/mmsh:/' rhythmdb.xml
```

This process can of course be automated such that a shell script containing the proxy setting and rhythmbox is started when starting rhythmbox from the Applications menu, but I think that starting it from a shell is an acceptable workaround until the problem is fixed in the code.

---

### Post by beow on 2008-07-30
For example: BBC World Service is found by using the URL:

```
mmsh://livewmstream-ws.bbc.co.uk.edgestreams.net/reflector:38288
```

using the method above.

---

### Post by sandeepraj on 2009-01-12
hi...
i'm a newbie to linux and i see ~/.bashrc file already exist in my computer 
do i over write it or add that code to existing one??

---

### Post by valavanisalex on 2009-03-10
Just add the text to the bottom

---

### Post by dajam on 2010-02-11
Even with the http_proxy variable correctly set in the shell launching rythmbox, the program is still not able to connect to cddb servers nore to download album visuals. 
However, it's perhaps because it tries to connect using cddb protocol and not through http ?

---

### Post by cbetts on 2010-03-29
> **dajam said:**
> 
However, it's perhaps because it tries to connect using cddb protocol and not through http ?

Looks like the cddb portion is doing it's own thing.  First it sends out a ping and then connects via http on port 80.  Is this issue caused by Rhythmbox or is it part of musicbrainz?

Everything else in Rhythmbox seems to use the proxy setting just fine.  It is just the cddb portion that is failing and not using the proxy environment.

---

