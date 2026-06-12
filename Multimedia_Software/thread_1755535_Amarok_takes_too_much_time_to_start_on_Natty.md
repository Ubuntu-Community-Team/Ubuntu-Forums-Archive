---
title: "Amarok takes too much time to start on Natty"
date: 2011-05-11
forum: Multimedia Software
---

### Post by jhahoneyk on 2011-05-11
Hi, I recently installed Kubuntu Natty 11.04 on my machine, everything works pretty cool, but Amarok takes a LOT of time to start, around one minute.

Output of amarok --debug contains this part where it takes ~50 secs doing nothing (stays blank after Collections::UpnpCollectionFactory::init() ), but I've no idea what it means -

```
amarok:           [CollectionManager] Initialising "upnp-collection" 
amarok:           BEGIN: virtual void Collections::UpnpCollectionFactory::init() 
unnamed app(16503): Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

shaan@shaan-laptop:~$ amarok:             [UpnpCollectionFactory] ERROR "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." 
amarok:           END__: virtual void Collections::UpnpCollectionFactory::init() [DELAY Took (quite long) 50s] 

```

Any idea how to fix this?

---

### Post by jhahoneyk on 2011-05-22
Fixed by upgrading amarok using the kubuntu backports ppa

---

