---
title: "Unhandled exception with Cowbell batch tagging"
date: 2009-05-20
forum: Multimedia Software
---

### Post by rare HERO on 2009-05-20
When I try to use Cowbell's Batch Tagging, the following error happens.
Who else has seen this and what did you do to fix it?

```
$ cowbell --batch /home/rene/Music
Searching /home/rene/Music/3 Doors Down/Away From The Sun...
Found /home/rene/Music/3 Doors Down/Away From The Sun

Unhandled Exception: System.ApplicationException: URI could not be converted to local file path
  at Cowbell.Base.SafeUri.UriToFilename (System.String uri) [0x00000] 
  at Cowbell.Base.Filesystem.Import (System.String[] uris) [0x00000] 
  at Cowbell.Base.Batch.ProcessAlbum (System.String dir) [0x00000] 
  at Cowbell.Base.Batch..ctor (System.String[] paths, Boolean quiet) [0x00000] 
  at Cowbell.Runtime.Main (System.String[] args) [0x00000] 
```

---

### Post by rare HERO on 2009-05-20
I also get this when attempting to run in debug

```
$ cowbell --debug
Debug mode enabled.
Loading preferences file from ~/.cowbell
TagLib: MPEG::Header::parse() -- Invalid sample rate.
GlobalDataModified called with song:
       Title: 
      Artist: American Head Charge
       Album: The War of Art
       Genre: Rock
 TrackNumber: 0
        Year: 2001
     Comment: 

The request failed with HTTP status 410: Gone
  at System.Web.Services.Protocols.SoapHttpClientProtocol.ReceiveResponse (System.Net.WebResponse response, System.Web.Services.Protocols.SoapClientMessage message, System.Web.Services.Protocols.SoapExtension[] extensions) [0x00000] 
  at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke (System.String method_name, System.Object[] parameters) [0x00000] 
  at Cowbell.Base.AmazonSearchService.ArtistSearchRequest (Cowbell.Base.ArtistRequest ArtistSearchRequest) [0x00000] 
  at (wrapper remoting-invoke-with-check) Cowbell.Base.AmazonSearchService:ArtistSearchRequest (Cowbell.Base.ArtistRequest)
  at Cowbell.AlbumCoverImage.GetCoverFromAmazon () [0x00000] 
  at Cowbell.AlbumCoverImage.AmazonDownload () [0x00000] 
The request failed with HTTP status 410: Gone
  at System.Web.Services.Protocols.SoapHttpClientProtocol.ReceiveResponse (System.Net.WebResponse response, System.Web.Services.Protocols.SoapClientMessage message, System.Web.Services.Protocols.SoapExtension[] extensions) [0x00000] 
  at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke (System.String method_name, System.Object[] parameters) [0x00000] 
  at Cowbell.Base.AmazonSearchService.ArtistSearchRequest (Cowbell.Base.ArtistRequest ArtistSearchRequest) [0x00000] 
  at (wrapper remoting-invoke-with-check) Cowbell.Base.AmazonSearchService:ArtistSearchRequest (Cowbell.Base.ArtistRequest)
  at Cowbell.AlbumCoverImage.GetCoverFromAmazon () [0x00000] 
  at Cowbell.AlbumCoverImage.AmazonDownload () [0x00000]
```

---

### Post by Routhinator on 2010-05-27
I'm going to bump this post as I also have the same issue with cowbell:

routh@routh-server:~$ cowbell --batch /srv/files/Music
Searching /srv/files/Music/2 Live Crew...
Found /srv/files/Music/2 Live Crew

Unhandled Exception: System.ApplicationException: URI could not be converted to local file path
  at Cowbell.Base.SafeUri.UriToFilename (System.String uri) [0x00000] 
  at Cowbell.Base.Filesystem.Import (System.String[] uris) [0x00000] 
  at Cowbell.Base.Batch.ProcessAlbum (System.String dir) [0x00000] 
  at Cowbell.Base.Batch..ctor (System.String[] paths, Boolean quiet) [0x00000] 
  at Cowbell.Runtime.Main (System.String[] args) [0x00000]

---

