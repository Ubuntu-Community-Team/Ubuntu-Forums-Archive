---
title: "[DLNA/UPNP] How to reduce streaming Pulseaudio output using Rygel?"
date: 2014-11-24
forum: Multimedia Software
---

### Post by hiteule on 2014-11-24
I followed this procedure to stream my Pulseaudio output into a dlna device (A Samsung TV) with Rygel : [https://wiki.gnome.org/Projects/Rygel/Pulseaudio](https://wiki.gnome.org/Projects/Rygel/Pulseaudio)
  It's working, but, I have a latency around 40 seconds. ):
  I'm on Unbuntu 14.10. Here, is my ~/.config/rygel.conf :

```

[GstLaunch]
enabled=true
launch-items=myaudioflac;myaudiompeg;myaudioraw

myaudioflac-title=FLAC audio on @HOSTNAME@
myaudioflac-mime=audio/flac
myaudioflac-launch=pulsesrc device=upnp.monitor throttle-time=100 ! flacenc
```


Is there a solution to have a correct latency (Arround 1 or 4 sec.) ?
  Thx !

---

### Post by qos2 on 2014-12-30
My experience with rygel was pretty bad.
For that reason i created pulseaudio-dlna.

Check it out and give it a try... you can find it here: [https://github.com/masmu/pulseaudio-dlna](https://github.com/masmu/pulseaudio-dlna)
I am using it with various devices and it works pretty well but i am curious to see if it also works with your samsung tv.

Btw, my latency is about 1-2 seconds.

If you need any help, don't hesitate to ask ;)

---

### Post by hiteule on 2015-01-01
Hi !

Thanks for yout help (:

I just try pulseaudio-dlna on a fresh install of ubuntu 14.10 but it don't work ):

I follow the installation procedure, turn on my Samsung TV and launch pulseaudio-dlna.
My tv was found, I launch music on my computer and I select my TV called "TV salon" on the sound config but nothing happend on my TV.

Here is the cli output :
> hiteule@bozo-laptop:~/pulseaudio-dlna$ ./pulseaudio_dlna.py --host=192.168.0.2
INFO:requests.packages.urllib3.connectionpool:Starting new HTTP connection (1): 192.168.0.4
INFO:root:found upnp_device "<CoinedUpnpMediaRenderer name="TV salon" short_name="tvsalon" state="idle">"
INFO:root:PulseWatcher.on_device_updated
INFO:requests.packages.urllib3.connectionpool:Starting new HTTP connection (1): 192.168.0.4
192.168.0.4 - - [01/Jan/2015 20:59:03] "HEAD /tvsalon.stream HTTP/1.0" 200 -
ERROR:root:"TV salon" registering failed!
INFO:requests.packages.urllib3.connectionpool:Starting new HTTP connection (1): 192.168.0.4
ERROR:root:"TV salon" playing failed!

Do you know what is the problem ?

Edit :
After a short debug session, the register method return this error :
> <s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" s:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"><s:Body><s:Fault><faultcode>s:Client</faultcode><faultstring>UPnPError</faultstring><detail><UPnPError xmlns="urn:schemas-upnp-org:control-1-0"><errorCode>716</errorCode><errorDescription>Resource not found</errorDescription></UPnPError></detail></s:Fault></s:Body></s:Envelope>

Here is the param posted to the url [http://192.168.0.4:52235/upnp/control/AVTransport1](http://192.168.0.4:52235/upnp/control/AVTransport1) :
> <?xml version="1.0" encoding="utf-8" standalone="yes"?>
<s:Envelope s:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
    <s:Body>
        <u:SetAVTransportURI xmlns:u="urn:schemas-upnp-org:service:AVTransport:1">
            <InstanceID>0</InstanceID>
            <CurrentURI>http://192.168.0.2:8080/salon.stream</CurrentURI>
            <CurrentURIMetaData>&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;DIDL-Lite xmlns="urn:schemas-upnp-org:metadata-1-0/DIDL-Lite/" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:dlna="urn:schemas-dlna-org:metadata-1-0/" xmlns:sec="http://www.sec.co.kr/" xmlns:upnp="urn:schemas-upnp-org:metadata-1-0/upnp/"&gt;
    &lt;item id="0" parentID="0" restricted="1"&gt;
        &lt;upnp:class&gt;object.item.audioItem.musicTrack&lt;/upnp:class&gt;
        &lt;dc:title&gt;Live Audio&lt;/dc:title&gt;
        &lt;dc:creator&gt;PulseAudio&lt;/dc:creator&gt;
        &lt;upnp:artist&gt;PulseAudio on bozo-laptop&lt;/upnp:artist&gt;
        &lt;upnp:albumArtURI&gt;&lt;/upnp:albumArtURI&gt;
        &lt;upnp:album&gt;Stream&lt;/upnp:album&gt;
        &lt;res protocolInfo="http-get:*:audio/mpeg:DLNA.ORG_OP=00;DLNA.ORG_FLAGS=01700000000000000000000000000000"&gt;[http://192.168.0.2:8080/salon.stream&lt;/res&gt;](http://192.168.0.2:8080/salon.stream&lt;/res&gt;)
    &lt;/item&gt;
&lt;/DIDL-Lite&gt;</CurrentURIMetaData>
        </u:SetAVTransportURI>
    </s:Body>
</s:Envelope>

When I open the url [http://192.168.0.2:8080/salon.stream]("http://192.168.0.2:8080/salon.stream&lt;/res&gt;") on another PC the stream work perfectly.

---

### Post by qos2 on 2015-01-04
Sorry for the late reply. I thought you get informed by email when someone replies to your post. :(

It seems that the Samsung TV does not like to structure of the XML request which normally registeres the UPNP renderer.

This shouldn't be a hard problem to fix, if i had one TV here. In the end you just have to adjust the REGISTER_XML and / or REGISTER_XML_METADATA.

Luckily, a friend of mine ownes one. Will see if i get my hands on it ;)

---

### Post by hiteule on 2015-01-04
Ok. Thanks again for your help !

During this time I'm looking for a solution about the xml too.

---

### Post by qos2 on 2015-01-04
Oh, cool ;)

I can give you some hints how to reproduce a successful registering.
There is a package named **gupnp-tools** which has 2 neat tools. one is **gupnp-av-cp** which can perform basic operations to upnp devices such as registering, playing, pause or stop.
Then you need a network sniffer named **wireshark**. I records your network traffic so that you can analyse whats really going on.
What you have to do is, first start wireshark and make sure that it is recording your current network traffic. After that start **gupnp-av-cp. **It should also detect your TV. Select your TV in **gupnp-av-cp. **This is the part where **gupnp-av-cp** should have registered your TV and therefore wireshark has recordered an XML register-request which acutally works with your TV. Note that there might be a confirmation dialog on your TV to allow the access to it, and you have to confirm this with your TV remote control.
Now you can stop wireshark from recording your network, but don't close it. Just stop the recording. It makes debugging easier.
In wireshark you can watch the packages which got recorded. Search for a POST request to your TV which should look like the one you did provide.
If you found it, you can compare it to the one pulseaudio-dlna does. **meld** is a good tool for that.

Good luck, and keep me posted. ;)

---

### Post by qos2 on 2015-01-04
Good news and bad news.

Good news are: I got my hands on the TV from my friend.
Bad news: It works without any problems. There is still this allow access confirmation dialog on the tv though. When you use it the first time you have to confirm it via the remote control.

It is a Samsung LED 60.

Which one is yours?

---

### Post by hiteule on 2015-01-12
Hi !

I work on it yesterday but after 2 hours It don't work ):
I think it's due to the non standart implementation of Samsung DLNA called "AllShare" on my TV.

I have correctly captured my network traffic when I push my music with Rygel and Upnp controll point. Here is two command line to push some music with curl :
```
curl -H 'SOAPAction:  "urn:schemas-upnp-org:service:AVTransport:1#SetAVTransportURI"' -H  'Content-Type: text/xml; charset="utf-8"' -X POST -d '<?xml  version="1.0"?><s:Envelope  xmlns:s=["http://schemas.xmlsoap.org/soap/envelope/"]("http://schemas.xmlsoap.org/soap/envelope/")  s:encodingStyle=["http://schemas.xmlsoap.org/soap/encoding/"]("http://schemas.xmlsoap.org/soap/encoding/")><s:Body><u:SetAVTransportURI  xmlns:u="urn:schemas-upnp-org:service:AVTransport:1"><InstanceID>0</InstanceID><CurrentURI>[http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D](http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D)</CurrentURI><CurrentURIMetaData>&lt;DIDL-Lite  xmlns=&quot;urn:schemas-upnp-org:metadata-1-0/DIDL-Lite/&quot;  xmlns:dlna=&quot;urn:schemas-dlna-org:metadata-1-0/&quot;  xmlns:dc=&quot;[http://purl.org/dc/elements/1.1/&quot](http://purl.org/dc/elements/1.1/&quot);  xmlns:upnp=&quot;urn:schemas-upnp-org:metadata-1-0/upnp/&quot;&gt;&lt;item  id=&quot;myaudiompeg&quot; parentID=&quot;0&quot;  restricted=&quot;0&quot;  dlna:dlnaManaged=&quot;00000004&quot;&gt;&lt;dc:title&gt;MPEG audio on  bozo-home&lt;/dc:title&gt;&lt;upnp:class&gt;object.item.audioItem&lt;/upnp:class&gt;&lt;res  protocolInfo=&quot;http-get:*:audio/mpeg:*&quot;&gt;[http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D&lt;/res&gt;&lt;res](http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D&lt;/res&gt;&lt;res)   protocolInfo=&quot;http-get:*:audio/mpeg:DLNA.ORG_PN=MP3;DLNA.ORG_CI=1;DLNA.ORG_FLAGS=01700000000000000000000000000000&quot;   bitrate=&quot;16000&quot;&gt;[http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D/tr/MP3.mp3&lt;/res&gt;&lt;res](http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D/tr/MP3.mp3&lt;/res&gt;&lt;res)   protocolInfo=&quot;http-get:*:audio/L16;rate=44100;channels=2:DLNA.ORG_PN=LPCM;DLNA.ORG_CI=1;DLNA.ORG_FLAGS=01700000000000000000000000000000&quot;   bitrate=&quot;176400&quot;  sampleFrequency=&quot;44100&quot;  nrAudioChannels=&quot;2&quot;  bitsPerSample=&quot;16&quot;&gt;[http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D/tr/LPCM.lpcm&lt;/res&gt;&lt;res](http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D/tr/LPCM.lpcm&lt;/res&gt;&lt;res)   protocolInfo=&quot;http-get:*:audio/vnd.dlna.adts:DLNA.ORG_PN=AAC_ADTS_320;DLNA.ORG_CI=1;DLNA.ORG_FLAGS=01700000000000000000000000000000&quot;   bitrate=&quot;32000&quot;&gt;[http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D/tr/AAC_ADTS_320.adts&lt;/res&gt;&lt;/item&gt;&lt;/DIDL-Lite&gt](http://192.168.0.1:36834/GstLaunch/i/bXlhdWRpb21wZWc%3D/tr/AAC_ADTS_320.adts&lt;/res&gt;&lt;/item&gt;&lt;/DIDL-Lite&gt);</CurrentURIMetaData></u:SetAVTransportURI></s:Body></s:Envelope>'  '[http://192.168.0.4:52235/upnp/control/AVTransport1](http://192.168.0.4:52235/upnp/control/AVTransport1)' -i

curl -H 'SOAPAction: "urn:schemas-upnp-org:service:AVTransport:1#Play"'  -H 'Content-Type: text/xml; charset="utf-8"' -X POST -d '<?xml  version="1.0"?><s:Envelope  xmlns:s=["http://schemas.xmlsoap.org/soap/envelope/"]("http://schemas.xmlsoap.org/soap/envelope/")  s:encodingStyle=["http://schemas.xmlsoap.org/soap/encoding/"]("http://schemas.xmlsoap.org/soap/encoding/")><s:Body><u:Play   xmlns:u="urn:schemas-upnp-org:service:AVTransport:1"><InstanceID>0</InstanceID><Speed>1</Speed></u:Play></s:Body></s:Envelope>'   '[http://192.168.0.4:52235/upnp/control/AVTransport1](http://192.168.0.4:52235/upnp/control/AVTransport1)' -i
```
(In fact it work like a charm without CurrentURIMetaData)
This cli work with any pc in my house.

I tried this same instruction many times with differents encoder, format etc. (obviously, I replaced all parts with the pulseaudio-dlna data server) and in any case I receive a 500 HTTP code with this error message : "...<errorCode>716</errorCode><errorDescription>Resource not found</errorDescription>..." ):

My TV is a Samsung LE32630K1W.

Anyway, yesterday evening I bough a DLink DCHM225. I have planned this purchase but i wanted to try the technical solution with my TV before.
I let you know if it work with pulseausio-dlna.

If you are interested I can give you my wireshark capture.

Thx for your intereset and your help (:
Hiteule.

---

### Post by hiteule on 2015-01-17
I receive my Dlink DCH-M225 and it work perfectly ! \o/
Verry good job !

---

### Post by qos2 on 2015-01-18
I am glad to hear that. But i am not done with getting your other devices to work :)

Just the get that right. If you remove the **<CurrentURIMetaData>** entry from the provided curl request it works with every device in your house? Also the ones which did not work before?

Could you provide me the capture?

---

### Post by hiteule on 2015-01-18
I'm don't try to remove <CurrentURIMetaData> node on another device (only with rygel on my pc with my Samsung TV).

You can find on attachement of this post the capture of dlna renderer with rygel and my Samsung TV. I push (register + play) the sound with Controll Point, wait ~30 sec to play the sound on my TV and stop it.

192.168.0.1 is my PC and 192.168.0.4 is my TV.

Good luck (;

---

### Post by qos2 on 2015-01-25
I got a hint from another bug report and maybe this will fix your issues too.

Could you please test the following branch?

[https://github.com/masmu/pulseaudio-dlna/tree/testing/renderer-incompatibility-fix-1](https://github.com/masmu/pulseaudio-dlna/tree/testing/renderer-incompatibility-fix-1)

---

### Post by hiteule on 2015-02-01
Hi,

I just test the following branch and it doesn't work with my Samsung TV. The error was exactly the same as before.

---

