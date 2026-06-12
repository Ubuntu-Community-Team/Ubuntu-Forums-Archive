---
title: "some issues isung banshee ... (proxy, videos, freeze ...)"
date: 2011-02-24
forum: Multimedia Software
---

### Post by Zib.c on 2011-02-24
Hi everybody,

I'm experiencing some issues with banshee ...
first of all I am behind a proxy server and banshee does not seem to take it into account although it is set up in the proxy config of gnome (and also gconf!)
secondly : from time to time banshee freezes want I stop the music while it is reduced to the system tray ... do somebody have experienced the same kind of bug ?
finally, I am trying to use banshee to read some HD series and full HD clips and ... it reads it quite well but at the end of the movie ... it freezes ...

the problem is that although I installed the debug symbols for banshee I do not have any stack trace of the freeze ...

thank you for your help

edit : except for the proxy configuration : 
```

Caught an exception - System.NotSupportedException: Proxy scheme not supported. (in `System')
  at System.Net.ServicePointManager.FindServicePoint (System.Uri address, IWebProxy proxy) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetServicePoint () [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.BeginGetResponse (System.AsyncCallback callback, System.Object state) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri, System.String[] ignoreMimeTypes) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MusicBrainz.MusicBrainzQueryJob.FindAsin () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MusicBrainz.MusicBrainzQueryJob.Lookup () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MusicBrainz.MusicBrainzQueryJob.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.Run () [0x00000] in <filename unknown>:0 

```

ps : I'm running 64bits maverick

---

### Post by asprasad on 2011-11-09
I am also having this issue :( On Ubuntu Oneric.

---

