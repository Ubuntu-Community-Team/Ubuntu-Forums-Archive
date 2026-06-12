---
title: "Codec Friendly Media Player or Converter"
date: 2010-02-27
forum: Multimedia Software
---

### Post by Martin Marshalek on 2010-02-27
So I am all set up and back in Ubuntu and, due to a thread I posted yesterday and a few searches, found that without paying for the fluendo codecs or switching to 32bit (for pitfdll with w32codecs) there is no way to get gstreamer to support WMA 9, 10, Pro, Lossless or WMV using those audio codecs. It seems however that Xine, Mplayer via w64codecs, VLC, and xmms2 (not sure about this one but I think so) all support or partially support at least WMA 9 (which is what I need). I have searched though and have not found one media player that is more Rhythmbox like as opposed to Totem like (geared more toward videos and DVD's). I realize that AmaroK works for these requirements but I would like to stick to Gtk. Are there any other media players that are like that that can use Xine and are gtk based? If not, how is xmms2 from the repos? If there is nothing like that then, is there a way for me to convert WMA 9 to ogg or mp3 without being able to decode it with gstreamer?

Thanks

---

### Post by Yellow Pasque on 2010-02-27
> Mplayer via w64codecs
AFAICT, w64codecs only contains 3 codecs - 2 from Real Networks, and one for DivX. It does not contain the .dll's needed for WMA.

> or switching to 32bit
It would be easier to make a 32-bit chroot. I used these directions: [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) (after you complete the "Setting up your chroot with debootstrap" section, skip to the "Setting up a dchroot (non-root) environment" section)

---

