---
title: "Sound Visualiser in Karmic: No playback"
date: 2009-12-18
forum: Multimedia Software
---

### Post by youoneah on 2009-12-18
Hi there,

Many music fans will have heard of [Sonic Visualiser]("http://www.sonicvisualiser.org/"), which is popular enough on 'buntu to have its own build, even a 64-bit. I installed sonic-visualiser_1.7.1cc-1_amd64.deb, and it worked without issues--inculding playback--though I was still using Intrepid.

As the story goes, I recently upgraded to Karmic by way of Jaunty just using the Update Manager, which also went without incident. I am booting via a static Grub entry on a Debian-managed partition, but I've updated it and am currently booting 2.6.31-16-generic. Sound is working for the system, but in Sonic Visualiser there is no playback.

Google did help me out: [topic on vamp forums]("http://vamp-plugins.org/forum/index.php?PHPSESSID=da68d3e1fb273d979c7342f98a650982&topic=129.msg318#msg318")
The speculation there is a conflict with pulseaudio. One suggested solution was to recompile; I attempted and failed.


This is what I get when launching from a terminal:
```
$ sonic-visualiser 
Registering interactive file finder
Loading qt_en_US... Failed
Failed to load Qt translation for locale
Loading sonic-visualiser_en_US... Done
ALSA lib seq.c:910:(snd_seq_open_conf) symbol _snd_seq_hw_open is not defined inside (null)

RtMidiIn::initialize: error creating ALSA sequencer input client object.


RtMidiIn::initialize: error creating ALSA sequencer input client object.

View::View(0x358c7c0)
View::View(0x3703cf0)
NOTE: Document::setModel: Layer 0x371c950 ("Ruler") is already set to model 0 ("(null)")
NOTE: Document::setModel: Layer 0x3773a00 ("Waveform") is already set to model 0 ("(null)")
Comparing current version "1.7.1" with latest version "1.7.1"
PluginRDFIndexer::reindex: NOTE: no vamp:Plugin resources found in indexed documents
PluginRDFIndexer::indexConfiguredURLs
PluginRDFIndexer::indexConfiguredURLs: index url is http://www.vamp-plugins.org/rdf/plugins/index.txt
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/index.txt"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:03 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/vamp-example-plugins
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/vamp-example-plugins"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:04 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/ofa-vamp-plugin
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/ofa-vamp-plugin"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:04 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/vamp-libxtract
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/vamp-libxtract"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:05 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/qm-vamp-plugins
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/qm-vamp-plugins"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:06 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/mazurka-plugins
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/mazurka-plugins"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:07 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/vamp-aubio
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/vamp-aubio"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:08 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/match-vamp-plugin
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/match-vamp-plugin"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:09 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/vamp-onsetsds
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/vamp-onsetsds"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:09 2009
PluginRDFIndexer::indexConfiguredURLs: url is http://www.vamp-plugins.org/rdf/plugins/mvamp
CachedFile::CachedFile: origin is "http://www.vamp-plugins.org/rdf/plugins/mvamp"
CachedFile::check: Valid last retrieval at Thu Dec 17 09:32:10 2009
OSCQueue::OSCQueue: Base OSC URL is osc.udp://lewis:10453/
Finished setting up OSC interface
```

Most of that is rubbish, but the ALSA-related error seems relevant.

If anyone else has dealt with this or similar issues, or can help me figure out a fix, I'd be much obliged.

---

### Post by youoneah on 2009-12-21
Bump.

If I am not asking the right questions, please help me do so. Hoping for some help, as I am not experienced resolving sound conflicts.

---

### Post by luctor on 2010-03-05
I've created a PPA for Sonic-Visualiser
[https://launchpad.net/~rghvdberg/+archive/sv](https://launchpad.net/~rghvdberg/+archive/sv)

> Sonic Visualiser is an application for viewing and analysing the contents of music audio files.
[http://sonicvisualiser.org/](http://sonicvisualiser.org/)

This PPA requires Philip Johnsson's ppa [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra) for dependencies. (librubberband ,vamp,liblo0)

---

### Post by stanlea on 2011-03-13
Just saw this thread and wanted to thank you a lot for the amd64 builds.

---

