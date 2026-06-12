---
title: "PVR150 or what? MythTV"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by samjaynes on 2007-02-06
Let me preface this post that I am a noob to Linux, and have sure enjoyed using the LiveCD thus far with Ubuntu.  I am looking to install Ubuntu and MythTV soon, and other than tuner cards, my computer seems fit for this.   I have spent several hours reading threads, and still am confused on what card would work best, for my experience, and use.

Since ATSC signal is broadcasted in my area, I would like to pick up these HD signals with the card ( Hauppauge PVR150, or what ).  Searching NewEgg.com results in no mention of ATSC reception, just the display of NTSC (picture quality loss?).  Several mentions lead to suggesting purchasing one or two PVR150's.  Although I see some different models.  Also, the buyer comments at NewEgg state that there may be a new chipset which inhibits the ability for ATSC reception, or incompatability with IVTV.

So, I leave this post open for your suggestions.  Thanks again for a great forum.

---

### Post by fenian on 2007-02-07
What you probably want is the pcHDTV card more info below...

[http://www.mythtv.org/wiki/index.php/PcHDTV_HD-3000](http://www.mythtv.org/wiki/index.php/PcHDTV_HD-3000)

[http://www.pchdtv.com/](http://www.pchdtv.com/)

---

### Post by samjaynes on 2007-02-07
Thanks for the info... I went to the site, and it appears that card does not have on-board encoding on it, thus resource intensive... Good or Bad?  And the company does not make the 3000, but a newer 5500 model.  I have e-mailed the company with questions.

Does the PVR150 pick up ATSC signals?  Just curious, as I am still trying to find the ideal card(s) for capturing the signal.  What about a front-end card to display on a analog TV for the time being?

---

### Post by fenian on 2007-02-07
The pvr 150 won't pickup ATSC .Here is a list of HDTV cards for mythtv...

[http://www.mythtv.org/wiki/index.php/Category:HDTV_capture_cards](http://www.mythtv.org/wiki/index.php/Category:HDTV_capture_cards)

Here's another one that looks o.k...

[http://www.newegg.com/Product/Product.asp?Item=N82E16815100134](http://www.newegg.com/Product/Product.asp?Item=N82E16815100134)

Also it is important to note that ATSC and DVB signals are sent in the MPEG2 transport stream and require no encoding on the tuner card.More info here...

[http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card)

---

### Post by majoridiot on 2007-02-07
as a heads up to everyone- i was reading a thread on the mythtvtalk forum and it seems that
the holiday season wiped out the PVR-150 supply and hauppauge is (or was) putting another
card in the 150 box with a little note explaining the situation.

the upside is that the card they replace it with is ATSC capable at no extra cost.

the downside is that it is NOT compatible with the IVTV drivers, so it's pretty much useless for
linux use at the moment.

if anyone plans on purchasing a PVR-150, you should probably do it locally, with a retailler that
will allow you to open the box to check before you buy (there's no way to tell until you open it)
or buy from an online retailler that has liberal open-box return policies.

i'm posting this as a stand-alone thread too- so hopefully it will be better seen.

---

### Post by punx45 on 2007-02-07
> **majoridiot said:**
> as a heads up to everyone- i was reading a thread on the mythtvtalk forum and it seems that
the holiday season wiped out the PVR-150 supply and hauppauge is (or was) putting another
card in the 150 box with a little note explaining the situation.

the upside is that the card they replace it with is ATSC capable at no extra cost.

the downside is that it is NOT compatible with the IVTV drivers, so it's pretty much useless for
linux use at the moment.

if anyone plans on purchasing a PVR-150, you should probably do it locally, with a retailler that
will allow you to open the box to check before you buy (there's no way to tell until you open it)
or buy from an online retailler that has liberal open-box return policies.

i'm posting this as a stand-alone thread too- so hopefully it will be better seen.

i noticed this was being mentioned in the newegg reviews lately.   i bought a PVR-150 from newegg mid-january and it has worked fine.

also to the thread starter.. you might want to consider an all-in one distro like Knoppmyth (debian, so ubuntuforums discussions will still be mostly applicable) or MythDora (fedora based).  you will get a base OS and MythTV install all in one shot with little effort.  certainly more n00b friendly :)

also, if you go with the PVR-150 card that has built in IR, you will need to install a patched version of the lirc IR driver to get the IR blaster (to control a cable/satellite box) and I have not been able to do so yet.   However, the IR reciever for the remote worked after the basic MythDora install (but then i broke it :/ )

---

### Post by peterthewolf on 2007-02-07
Many of the problems talked about would disappear if the various linux developers started looking at what one another does. I have a DVB-T card, works fine with Kaffiene but Mythtv forget it.

---

