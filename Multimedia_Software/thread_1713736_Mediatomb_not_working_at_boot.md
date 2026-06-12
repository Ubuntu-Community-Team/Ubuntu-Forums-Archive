---
title: "Mediatomb not working at boot"
date: 2011-03-24
forum: Multimedia Software
---

### Post by ubunfish on 2011-03-24
Hello, I just rebuilt a server I had mediatomb running on from fedora 13 to ubuntu server 10.10 x64.  I have most everything up and running now the way I want it, however I'm having a problem of getting the upnp devices (dlink picture frames) to see the mediatomb upnp resources after a server reboot.  I've read all the posts about mediatomb starting before the network interfaces were up, so I changed the run order as described in another post to 99 for mediatomb using:

```


sudo update-rc.d mediatomb remove

sudo update-rc.d mediatomb defaults 99


```

Looking in /etc/rc2.d (I've verified that it's booting in runlevel 2) I can verify that mediatomb was set to 99.  I verify there's a pid and if I look in /var/log/mediatomb.log it says it starts fine and is listening with no errors:

```


2011-03-24 11:17:12    INFO: Loading configuration from: /etc/mediatomb/config.xml
2011-03-24 11:17:12    INFO: Checking configuration...
2011-03-24 11:17:12    INFO: Setting filesystem import charset to UTF-8
2011-03-24 11:17:12    INFO: Setting metadata import charset to UTF-8
2011-03-24 11:17:12    INFO: Setting playlist charset to UTF-8
2011-03-24 11:17:12 WARNING: You enabled the YouTube feature, which allows you
                             to watch YouTube videos on your UPnP device!
                             Please check http://www.youtube.com/t/terms
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2011-03-24 11:17:12    INFO: Configuration check succeeded.
2011-03-24 11:17:12    INFO: Initialized port: 49153
2011-03-24 11:17:12    INFO: Server bound to: 10.5.1.10
2011-03-24 11:17:13    INFO: MediaTomb Web UI can be reached by following this link:
2011-03-24 11:17:13    INFO: http://10.5.1.10:49153/


```

(this youtube message is another thing.  I have it set to NO in the config.xml and it still says it's enabled.  Don't know why)

However, my dlink picture frames still do not see the upnp server mediatomb unless I log in and do

sudo service mediatomb restart

Then they come right up.  When I had this running on the fedora 13 box, it worked fine at boot after changing the boot order, but not so good on this ubuntu box.

Is there anything else I can check?  I'm out of ideas.

Thanks!

---

