---
title: "can't play mp3's"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by scuba_suit on 2007-11-01
tried going by what it said in the sticy, i got edubuntu and when i went to add/remove programs couldn't find gstreamer, i dl'ed some tracks in mp3 and of course couldn't hear them, what can i use to hear them?

---

### Post by MrFSL on 2007-11-02
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

That should give you your answer.

Really if you search the wonderful Online and Community documentation, as well as search this very forum you would get your answer much faster.

---

### Post by ZOMGxuan on 2007-11-02
Are you sure you can't find them? They should be under the sound and video catergory.

[[IMG]http://img469.imageshack.us/img469/8240/gstreameraddremoveapplixa6.th.png[/IMG]](http://img469.imageshack.us/my.php?image=gstreameraddremoveapplixa6.png)

If you still can't find them, try checking whether you have all repositories enabled in Synaptic Package Manager (System>Administration>Synaptic Package Manager), by going to Settings>Repositories and making sure that main and multiverse are checked. They should be by default. Then do a search for gstreamer in synaptic and download the neccessary plugins (If you don't know which just download all i.e. the base, the good, the bad and the ugly). I don't know if Edubuntu is different from normal ubuntu, but this is what would work on ubuntu.

If all still fails, just download a media player which does not use Gstreamer.

---

