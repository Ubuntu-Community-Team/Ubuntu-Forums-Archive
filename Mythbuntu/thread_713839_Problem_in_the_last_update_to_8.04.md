---
title: "Problem in the last update to 8.04"
date: 2008-03-03
forum: Mythbuntu
---

### Post by wombo on 2008-03-03
I updated this morning ok, but I thought I would give it another go tonight only to be faced with the following errors.

Note that I could not see the top bit in my SSH window, but from memory it was all ok.

```
Setting up mythtv-transcode-utils (0.21.0~fixes16338-0ubuntu1) ...
Setting up mythtv-backend (0.21.0~fixes16338-0ubuntu1) ...
Installing new version of config file /etc/default/mythtv-backend ...
Installing new version of config file /etc/init.d/mythtv-backend ...
udev active, devices will be created in /dev/.static/dev/
 * Starting MythTV server: mythbackend                                   [ OK ]

Setting up mythtv-database (0.21.0~fixes16338-0ubuntu1) ...

Setting up mythtv-backend-master (0.21.0~fixes16338-0ubuntu1) ...
Setting up mythtv-frontend (0.21.0~fixes16338-0ubuntu1) ...
chmod: invalid argument: `'
dpkg: error processing mythtv-frontend (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-frontend (= 0.21.0~fixes16338-0ubuntu1); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Setting up libmyth-python (0.21.0~fixes16338-0ubuntu1) ...

Setting up mytharchive-data (0.21.0~fixes16338-0ubuntu1) ...
Setting up mytharchive (0.21.0~fixes16338-0ubuntu1) ...
dpkg: dependency problems prevent configuration of mythbrowser:
 mythbrowser depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythbrowser (--configure):
 dependency problems - leaving unconfigured
Setting up mythbuntu-control-centre (0.23-0ubuntu1) ...

dpkg: dependency problems prevent configuration of mythcontrols:
 mythcontrols depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythcontrols (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgallery:
 mythgallery depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgallery (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnews:
 mythnews depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythnews (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythphone:
 mythphone depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythphone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythvideo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythweather:
 mythweather depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythweather (--configure):
 dependency problems - leaving unconfigured
Setting up mythweb (0.21.0~fixes16338-0ubuntu1) ...
 * Reloading web server config apache2                                                                                                          apache2: Could not reliably determine the server's fully qualified domain name,                                                                 using 127.0.1.1 for ServerName
                                                                         [ OK ]

dpkg: dependency problems prevent configuration of mythmusic:
 mythmusic depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmusic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mythtv-frontend
 mythtv
 mythbrowser
 mythcontrols
 mythgallery
 mythnews
 mythphone
 mythvideo
 mythweather
 mythmusic
E: Sub-process /usr/bin/dpkg returned an error code (1)
htpc@mythtv:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mythtv-frontend (0.21.0~fixes16338-0ubuntu1) ...
chmod: invalid argument: `'
dpkg: error processing mythtv-frontend (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-frontend (= 0.21.0~fixes16338-0ubuntu1); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythbrowser:
 mythbrowser depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythbrowser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythcontrols:
 mythcontrols depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythcontrols (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgallery:
 mythgallery depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythgallery (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythnews:
 mythnews depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythnews (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythphone:
 mythphone depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythphone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythvideo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythweather:
 mythweather depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythweather (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythmusic:
 mythmusic depends on mythtv-frontend (>= 0.20-0.0); however:
  Package mythtv-frontend is not configured yet.
dpkg: error processing mythmusic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-frontend
 mythtv
 mythbrowser
 mythcontrols
 mythgallery
 mythnews
 mythphone
 mythvideo
 mythweather
 mythmusic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


EDIT: Mines AMD64 as well

---

### Post by crp724 on 2008-03-03
I have the exact same problem on updating the amd64 builds of 8.04 mythbuntu around 7AM eastern.

Should we just wait for an update?

---

### Post by wombo on 2008-03-03
Looks like the dependancies are broken or something. saying that it needs the old version on some packages.

---

### Post by superm1 on 2008-03-03
<beavis_> superm1: today's mythtv-frontend fails because of a wrong chmod command in mythtv-frontend.postinst
<beavis_> superm1: I commented out the line chmod 2775 "$dir" and the apt-get upgrade worked again
<beavis_> just fyi
<superm1> ugh gosh.
<superm1> thanks beavis

Sent an update for it.  Sorry for the mistake folks.

---

### Post by wombo on 2008-03-03
Do we need to do anything special to run it this time. Or just wait a while for the fix to filter through?

Thanks

---

### Post by superm1 on 2008-03-03
It will filter through on it's own.  Finished building ~hr ago.
[https://edge.launchpad.net/ubuntu/+source/mythtv/0.21.0~fixes16338-0ubuntu2](https://edge.launchpad.net/ubuntu/+source/mythtv/0.21.0~fixes16338-0ubuntu2)

---

