---
title: "lubuntu 14.04 - k9copy / handbrake misbehaving"
date: 2016-01-29
forum: Multimedia Software
---

### Post by rebeltaz on 2016-01-29
Under lubuntu 14.04LTS, I cannot get k9copy or handbrake to work correctly. The work great under an existing ubuntu 10.04 system, but I am trying to set up a dedicated system...

I have installed libdvdread4 and libdvdnav4 as well as ubuntu-restricted-extras. I installed vlc and it plays DVDs fine. I then installed k9copy and handbrake, both through their PPAs. k9copy keeps saying that it cannot read the DVD. Handbrake will encode directly from the DVD or from an existing ISO image created by the k9copy on the 10.04 system, but the only encode option is mkv - no mp4 options available. 

I need k9copy so that I can rip a disc and encode it later at my own leisure. 

I need handbrake to encode to mp4.

Help?


-=[edit]=-
Apparently I am supposed to "edit" instead of replying to my own thread, so....

I managed to get handbrake to do mp4. I purged handbrake and installed handbrake-gtk. That refused to happen until I manually installed gstreamer1.0-plugin-bad. Once I did that and installed handbrake-gtk, I am once again presented with the mp4 option. So I'm good there, but I do still need help with k9copy. Or an alternative program to achieve the same result. Thanks.

---

### Post by Rob Sayer on 2016-01-31
Which ppa did you use?  I'm not sure there is one for k9copy that's stable for your release.

Read the first answer here:

[http://askubuntu.com/questions/538217/how-to-install-k9copy-in-14-04](http://askubuntu.com/questions/538217/how-to-install-k9copy-in-14-04)

And I'm wondering why you installed handbrake from a ppa.  It should be in the tested repos.  Which ppa?  Is there something in a newer version that is so necessary that it'd be worth installing an unsupported version?

I have 2 linux installs and the only ppas on either of them is for HEVC playback with SMplayer and VLC.  I can't think of any reason I'd want more of them.

---

### Post by rebeltaz on 2016-01-31
I'm sorry. You are correct in that 9copy is no longer supported and is no longer int he repository. I should have said k9copy-reloaded - [http://tomtomtom.org/k9copy-reloaded/en.html](http://tomtomtom.org/k9copy-reloaded/en.html) - ppa:tomtomtom/k9copy - but I wasn't thinking. I have this installed on my laptop running ubuntu 14.04 LTS and it works fine there.

As for handbrake, installing from the repositories, I didn't have mp4 support. Researching the net I came across several site suggesting to use the PPA. After I did that, it worked fine. Something having to do with handbrake not using encoder options available system wide, but instead using options built-in... I don't know but it worked, so...The PPA for that is ppa:stebbins/handbrake-releases

---

### Post by Rob Sayer on 2016-02-02
DId you install ubuntu-restricted-extras?  Because that handbrake bug may have been fixed by now.

The problem with k9copy may have something to do with copy protection.  I haven't ripped a DVD for a while now but I'm not sure that linux apps are all that up to date with newer dvd encryption.  You could try dvdfab hd decrypter in wine, and according to this it works pretty well:

[https://appdb.winehq.org/objectManager.php?sClass=application&iId=2377](https://appdb.winehq.org/objectManager.php?sClass=application&iId=2377)

There's something in the ubuntu wikis about ripping protected dvds but it's a little out of date.

---

### Post by rebeltaz on 2016-02-02
I did install ubuntu-restricted-extras, yes. k9copy still works fine under my 10.04, but the dependencies are no longer available under 10.04 to read dvds (in the repositories anyway), so I can't use that on a new system... I'll look at dvdfab, but I really don't like running win prorams unless I HAVE to. Thanks...

---

### Post by rebeltaz on 2016-02-03
Got it.... I swear I ran this code - I know I did - but... I ran it again and boom! DVD access!

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I don't know why it worked now and didn't before but I thank you all for your time.

---

