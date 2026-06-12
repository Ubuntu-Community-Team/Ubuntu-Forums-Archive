---
title: "WMV File does not Play"
date: 2009-01-09
forum: Multimedia Software
---

### Post by halw on 2009-01-09
Running U8.04 w/Firefox 3.0.5. Received an email with a wmv file attached and when I open it instead of asking to open with Totem all I get is a dialog as to whether or not I want to save.

In U7.10 w/FF2 I am able to open and play the file. I thought this might be a firefox issue until I was able to play the file using Mepis 8rc1 w/FF3.0.3.

I believe I have all the necessary plugins,such as gstreamer extras, etc. loaded. Not sure where to look next.

Any tips are appreciated.

---

### Post by binbash on 2009-01-09
i suggest installing mozilla-plugin-vlc

---

### Post by halw on 2009-01-09
> **binbash said:**
> i suggest installing mozilla-plugin-vlc

Thanks for the suggestion. However it didn't work.

---

### Post by wolfen69 on 2009-01-09
you need to install the w32codecs. do (if using ubuntu 8.10) if using another version of ubuntu, substitute intrepid with hardy, gutsy, etc.
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
then search synaptic for w32codecs.

---

### Post by halw on 2009-01-09
W32codecs one of the first things installed after OS install and updates.

The issue isn't that Totem won't open the wmv attachment. It is that the option to open it isn't there. See attached screen shot.

---

### Post by wolfen69 on 2009-01-09
just save it, *then* open it. otherwise, i don't understand.

---

### Post by halw on 2009-01-10
The issue is, I've always been able to open these files without saving them prior to 8.04/FF3. Would like to have that functionality continue in further versions of Ubuntu.

Furthermore, this isn't a problem with other distro's, e.g. Mepis

---

