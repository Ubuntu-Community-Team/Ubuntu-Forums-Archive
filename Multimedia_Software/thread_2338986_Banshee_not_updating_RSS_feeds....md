---
title: "Banshee not updating RSS feeds..."
date: 2016-10-03
forum: Multimedia Software
---

### Post by driebel on 2016-10-03
Banshee (2.6.2) does not seem to be able to read and update RSS feeds.  When I attempt to add an RSS feed, All I get is a "Network Error updating feed" message, and the feed does not download.

I know the feed itself is valid because it successfully updates on my phone using the BeyondPod Android app.  Is here a known issue with Banshee?

---

### Post by driebel on 2016-10-03
I found the following entry in the banshee log file.  I don't know if it';s really relevant, but it seems to concern podcasting and server connections:
[Warn  14:50:01.503] Caught an exception - Mono.Security.Protocol.Tls.TlsException: Invalid certificate received from server. Error code: 0xffffffff800b010a (in `Mono.Security')
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.RemoteValidation (Mono.Security.Protocol.Tls.ClientContext context, AlertDescription description) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.validateCertificates (Mono.Security.X509.X509CertificateCollection certificates) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.ProcessAsTls1 () [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.HandshakeMessage.Process () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Security.Protocol.Tls.Handshake.HandshakeMessage:Process ()
  at Mono.Security.Protocol.Tls.ClientRecordProtocol.ProcessHandshakeMessage (Mono.Security.Protocol.Tls.TlsStream handMsg) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.RecordProtocol.InternalReceiveRecordCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
System.IO.IOException: The authentication or decryption has failed. (in `Mono.Security')
  at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHandshakeCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
System.Net.WebException: Error getting response stream (Write: The authentication or decryption has failed.): SendFailure (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri, System.String[] ignoreMimeTypes) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.SaveHttpStream (System.Uri uri, System.String path, System.String[] ignoreMimeTypes) [0x00000] in <filename unknown>:0 
  at Banshee.Metadata.MetadataServiceJob.SaveHttpStreamCover (System.Uri uri, System.String albumArtistId, System.String[] ignoreMimeTypes) [0x00000] in <filename unknown>:0 
  at Banshee.Podcasting.PodcastImageFetchJob.Fetch () [0x00000] in <filename unknown>:0 
  at Banshee.Podcasting.PodcastImageFetchJob.Run () [0x00000] in <filename unknown>:0 
  at Banshee.Kernel.Scheduler.ProcessJobThread () [0x00000] in <filename unknown>:0

---

