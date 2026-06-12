---
title: "VLC Installation Problem"
date: 2008-06-26
forum: Multimedia Software
---

### Post by pjrodz on 2008-06-26
Hi! I recently installed Hardy and I'm having problems when I try to install VLC. I get the ff message:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb)
  Hash Sum mismatch


any ideas? Thanks!

---

### Post by Vivaldi Gloria on 2008-06-27
Why don't you use synaptic to install vlc? On the top panel choose

System > Admin. > Synaptic

Then from the settings menu click repositories and enable restricted & multiverse repositories.

Click refresh.

Search and install vlc.

---

### Post by wolfen69 on 2008-06-27
install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos *then* install vlc.

---

### Post by Vivaldi Gloria on 2008-06-27
> **wolfen69 said:**
> install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos *then* install vlc.

Why? vlc is not in medibuntu, see

[http://www.medibuntu.org/packages.php](http://www.medibuntu.org/packages.php)

It's in multiverse.

---

### Post by JohoTehAzn on 2008-06-27
Yeah, just use Synaptic to install VLC.  I don't recall ever having a problem like this.

---

### Post by pjrodz on 2008-06-28
> **JohoTehAzn said:**
> Yeah, just use Synaptic to install VLC.  I don't recall ever having a problem like this.

I did try using synaptic and I encountered the same problem. Maybe something's wrong with the vlc files in the repo?

---

### Post by mc4man on 2008-06-28
Your issue seems to be installing this
[http://packages.ubuntu.com/hardy/libwxbase2.6-0](http://packages.ubuntu.com/hardy/libwxbase2.6-0)
Either try directly from link or in synaptic 
if it doesn't install the error message may help you resolve the conflict(s)

Edit: ck. in synaptic and see if you have it and libwxgtk installed and if so what version

---

### Post by pjrodz on 2008-07-02
> **mc4man said:**
> Your issue seems to be installing this
[http://packages.ubuntu.com/hardy/libwxbase2.6-0](http://packages.ubuntu.com/hardy/libwxbase2.6-0)
Either try directly from link or in synaptic 
if it doesn't install the error message may help you resolve the conflict(s)

Edit: ck. in synaptic and see if you have it and libwxgtk installed and if so what version

It still doesn't work, and I get the same error message. Maybe there is something wrong with the files in the repositories? If so, who do we inform? Thanks!

---

