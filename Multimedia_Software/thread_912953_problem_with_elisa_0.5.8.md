---
title: "problem with elisa 0.5.8"
date: 2008-09-07
forum: Multimedia Software
---

### Post by x20mar on 2008-09-07
Hi,

I've been having some issues with elisa and I was wondering if someone could help me out.

I seem to be missing a lot of functionality from elisa such as youtube and flickr searching and it won't detect my upnp media server. Here's the error output

```
WARN  MainThread      plugin_registry             Sep 07 14:21:45  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      gst_metadata_slave_process_protocol Sep 07 14:21:46  Starting Slave-2 on unix:/tmp/elisa-metadata-SoGZLA.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Sep 07 14:21:46  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
WARN  MainThread      resource_manager            Sep 07 14:21:46  Creating youtube.resource_provider:YoutubeResourceProvider failed. A full traceback can be found at /tmp/elisa_FmNNYq.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Sep 07 14:21:46  Creating shoutcast.shoutcast_resource:ShoutcastResource failed. A full traceback can be found at /tmp/elisa_Z-9KDQ.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Sep 07 14:21:46  Creating flickr.resource_provider:FlickrResourceProvider failed. A full traceback can be found at /tmp/elisa_o_hYUv.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Sep 07 14:21:46  Creating wmd.wmd_resource:WMDResource failed. A full traceback can be found at /tmp/elisa_F5T5W_.txt (elisa/core/manager.py:83)
WARN  coherence                   Sep 07 14:21:46  Coherence UPnP framework version 0.5.8 starting... (coherence/base.py:251)
WARN  webserver                   Sep 07 14:21:46  WebServer on port 35618 ready (coherence/base.py:106)
WARN  MainThread      resource_manager            Sep 07 14:21:46  Creating smbwin32.smbwin32_resource:SmbWin32Resource failed. A full traceback can be found at /tmp/elisa_BO-ncv.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Sep 07 14:21:47  Creating osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_t6-g38.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Sep 07 14:21:47  Creating winremote.streamzap_input:StreamzapInput failed. A full traceback can be found at /tmp/elisa_SgqkRJ.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Sep 07 14:21:47  Creating lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_LSNgQf.txt (elisa/core/manager.py:83)
WARNING:root:Cannot find theme file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/widgets/styles.conf
WARNING:root:Cannot find resource file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/widgets/resources.conf
WARNING:root:Cannot find theme configuration files
WARN  MainThread      gst_metadata_slave_process_protocol Sep 07 14:21:48  Starting Slave-6 on unix:/tmp/elisa-metadata-g8QGlK.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-6 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Sep 07 14:21:48  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-6 stderr) (elisa/plugins/amp/master.py:57)
WARN  service_client              Sep 07 14:21:48  error requesting'http://192.168.2.1:80/http://192.168.2.1:80/serv1.xml' (coherence/upnp/core/service.py:314)
WARN  service_client              Sep 07 14:21:48  error requesting'http://192.168.2.1:80/http://192.168.2.1:80/serv1.xml' (coherence/upnp/core/service.py:314)
WARN  service_client              Sep 07 14:21:48  error requesting'http://192.168.2.1:80/http://192.168.2.1:80/serv2.xml' (coherence/upnp/core/service.py:314)
WARN  service_client              Sep 07 14:21:48  error requesting'http://192.168.2.1:80/http://192.168.2.1:80/serv3.xml' (coherence/upnp/core/service.py:314)
WARNING:root:Cannot find theme file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/base/styles.conf
WARNING:root:Cannot find resource file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/base/resources.conf
WARNING:root:Cannot find theme configuration files
WARN  MainThread      application                 Sep 07 14:21:50  An Traceback occurred and got saved to /tmp/elisa_PZKuv5.txt (elisa/core/application.py:316)
WARN  MainThread      filtered_shares_resource    Sep 07 14:21:52  smb:// not found. (elisa/plugins/filtered_shares/filtered_shares_resource.py:75)
WARN  Dummy-2         application                 Sep 07 14:21:53  An Traceback occurred and got saved to /tmp/elisa_J1DBVf.txt (elisa/core/application.py:316)
WARN  Dummy-2         application                 Sep 07 14:21:54  An Traceback occurred and got saved to /tmp/elisa_I_VNYW.txt (elisa/core/application.py:316)
WARN  coherence                   Sep 07 14:22:26  Coherence UPnP framework shutdown (coherence/base.py:423)
WARN  coherence                   Sep 07 14:22:26  Coherence UPnP framework shutdown (coherence/base.py:423)
WARN  MainThread      gst_metadata_master         Sep 07 14:22:26  restarting slave (elisa/plugins/gstreamer/amp_master.py:157)
WARN  MainThread      gst_metadata_master         Sep 07 14:22:26  restarting slave (elisa/plugins/gstreamer/amp_master.py:157)

```

If anyone can help me with this then please do

Many Thanks

---

### Post by genjosanzo on 2008-09-08
I have more or less the same issue, the only result in launching elisa is a black screen. I tried to install it on a windows powered computer in my office but the result is even worse:no windows at all appears.
Any suggestion?

---

### Post by bve on 2008-09-11
There were in previous versions of Elisa a few dependencies that were not documented - I found these in the tracebacks in /tmp/elisa_* files.

I have had no luck with upnp and Elisa, I too get these messages when starting Elisa:
```

WARN  MainThread      plugin_registry             Sep 07 14:21:45  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)

```

I don't think it is an issue with Coherence since using the Totem Coherence plugin I can find MediaTomb, to me this suggests the problem lies in Elisa.

The black screen if I recall correctly was related to a missing dependency on python-cssutils I think - I did post something on the Elisa forums about this for someone else:
[http://elisa.fluendo.com/forums/viewtopic.php?id=713](http://elisa.fluendo.com/forums/viewtopic.php?id=713) where he also referenced this:
[http://ubuntuforums.org/showpost.php?p=5556153&postcount=17](http://ubuntuforums.org/showpost.php?p=5556153&postcount=17)

---

