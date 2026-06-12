---
title: "basic question about tuner cards"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by dcherryholmes on 2007-11-08
So I'm building my first myth box (combined front and back end), and looking for advice about cards.  These are my needs:

-- receive "regular" (sorry, I'm a tard about this stuff) cable from Time Warner Cable in the Raleigh/Durham, NC area.

-- also be able to handle HD channels, down the road when I get an HD TV.

-- a remote would be nice, but I could choose a case that has the IR controller built in, or add one via a PCI or USB port

-- FM receiver

-- output video other than MPEG-2, so that mythvideo, mythmusic, mythgame can function.

I'm just a little confused whether the "HD" cards I've been reading about (looking at an  AVerMedia AVerTVHD MCE A180) will also take non-HD signals.  If anybody can recommend a particular card, that would be even better.

---

### Post by newlinux on 2007-11-09
Some information.

It isn't a simple matter of HD vs Non HD tv card signals. It is really digital vs analog.  All HD will be translated digital via cable (QAM) or over the air (OTA/ATSC). However, not all digital stations are HD. For instance, in my area, my cable company sends through unencrypted QAM (digital) HD and non-HD versions of the local channels. An Avermedia A180 (which has a QAM tuner) would be able to pick up both versions because it can tune non encrypted digital stations.

Analog is a whole different thing however. The Avermedia A180 does not have an analog  (NTSC) tuner and will not pick up any analog stations. 

What stations you can get via a QAM tuner depends on what stations your cable provider transmits unencrypted via QAM. You should find this out before counting on a QAM tuner. It is reasonable to expect all of your locals to transmitted via QAM.

The analog signals you can get now are the ones TV sets and VCRs have been able to get without a cable box for years. New TV's (HDTVs) often have QAM tuners, but older TVs have NTSC (analog) tuners. Anything an analog tv can tune can be gotten with an analog tuner card. In my opinion, the best analog tuner card is the Hauppage PVR-150, which can also be used to record from your cable box like a VCR would. 

Hope this helps. There is a lot more to know about tuners, if you have questions, just ask.

---

### Post by dcherryholmes on 2007-11-11
Wow.  Thanks a whole lot for that helpful reply.  I'm sure I'll have more questions as I work on this project, which I'll post here.

---

