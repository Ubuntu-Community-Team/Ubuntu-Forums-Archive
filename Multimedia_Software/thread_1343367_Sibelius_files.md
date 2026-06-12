---
title: "Sibelius files"
date: 2009-12-01
forum: Multimedia Software
---

### Post by tonymoloney on 2009-12-01
A friend has sent me a Sibelius composition in the form of a Sibelius file (*.sib)

For obvious reasons, I don't have Sibelius on my system,

Is there any application that can open a Sibelius file, like OpenOffice.org can open a MSWord file?

---

### Post by ad_267 on 2009-12-01
Unfortunately, no. You'll have to ask for the file in a different format or install Sibelius on a dual boot or VM.

---

### Post by tonymoloney on 2009-12-01
OK. Thanks.

---

### Post by Lars Noodén on 2009-12-02
If you dual boot to use Sibelius, OS X can read EXT partitions with a bit of extra work.  It is easier to install hfsplus, hfstools, and hfsutils in Ubuntu and make an HFS partition or mount the OS X one.  An HFS partition made in Ubuntu will show up as another disk in OS X.  

Rosegarden can read MIDI, but not sibelius.

MuseScore, Noteedit and Canorus can import MIDI and MusicXML

Denemo / Lilypond can read lilypond and MIDI


MusicXML is a new format to me.  Is it able to work for your music and could Sibelius export to it?

---

### Post by cascade9 on 2009-12-02
> **Lars Noodén said:**
> MusicXML is a new format to me.  Is it able to work for your music and could Sibelius export to it?

It can, with an over priced plugin ($199!). Dolet 5- 

[http://www.recordare.com/sibelius/](http://www.recordare.com/sibelius/)

---

### Post by Farmers on 2010-09-17
Hi

I have a similar problem and was wondering if there has been any update on this as this thread was originally posted quite some time ago

Thanks!

---

### Post by ad_267 on 2010-09-17
Nope, still no Sibelius for Linux. There are applications that do a similar job but none that will open Sibelius files.

---

### Post by mathiaho on 2010-10-21
Hi

It's possible to install and run Sibelius under wine. It works flawlessly at my computer. I have made a guide here: [http://ubuntuforums.org/showthread.php?p=9848861](http://ubuntuforums.org/showthread.php?p=9848861)

It's for Sibelius 5, but I think it might work for other editions too. If it does, please let me know!

---

### Post by lazylew on 2010-11-04
> **Farmers said:**
> Hi

I have a similar problem and was wondering if there has been any update on this as this thread was originally posted quite some time ago

Thanks!I recently did a workaround for converting sib-files.
Export sib-files as musicPDF (won't work with "regular" pdf's) and convert them to music-xml with 
[http://www.myriad-online.com/en/products/pdftomusic.htm](http://www.myriad-online.com/en/products/pdftomusic.htm) 
(has trial ware)
then import those in Musescore, which is much like Sibelius.
It's simpler but it's free of charge as well.

I hope this helps, because I don't remember more details of how I successfully did this.

---

### Post by tpapastylianou on 2012-04-23
Sorry for arriving a bit late to the party.
There are now a number of plugins for sibelius to export directly to lilypond format.

A simple 'lilypond sibelius' google search throws a couple up on the top hits. (e.g. [http://www.sidorefa.com/sib2ly/](http://www.sidorefa.com/sib2ly/) and [http://scramblelovers.com/lilypond/](http://scramblelovers.com/lilypond/) )

These won't help you to convert a .sib file from ubuntu, but at least your friend can use the plugin to send you a .ly file directly.

Disclaimer: I haven't tried these myself. I'd be interested to hear how well they work in fact.

---

### Post by oldos2er on 2012-04-23
Old thread closed.

---

