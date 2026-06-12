---
title: "Can't get Audio/Vide presentation to play"
date: 2009-04-18
forum: Multimedia Software
---

### Post by dunbrokin on 2009-04-18
Can anybody get this to play in Ubuntu....I cannot get it to play in Ubuntu or in Widoze via Wine/Crossover.

[http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/lobby.aspx?Event_ID=630](http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/lobby.aspx?Event_ID=630)

Cross posted to Absolute Beginners Forum

---

### Post by wolfen69 on 2009-04-18
don't work for me. you might have to install windows in virtualbox to use it.

---

### Post by dunbrokin on 2009-04-18
> **wolfen69 said:**
> don't work for me. you might have to install windows in virtualbox to use it.



No way Hose!......we must be able to do better than that surely.

---

### Post by andrew.46 on 2009-04-18
Hi,

Well it is an asx stream which means it has a playlist type structure so the url:

[http://audability.com/events/test-stream.asx](http://audability.com/events/test-stream.asx)

eventually redirects to:

mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma

Have a look at the .asx file itself with a text editor and you will see all of the details:

```

<asx version = "3.0">

   <title>Webcast System Test</title>

   <author>Audability</author>

   <copyright>Audability</copyright>

   <entry>

      <title>Webcast System Test</title>

      <Author>Audability</Author>

      <copyright>Audability</copyright>

	  <ref href = "rtsp://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma"/>

          <ref href = "mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma"/>

	  <ref href = "http://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma"/>

   </entry>

</asx>

```

This plays well enough with MPlayer:

```

andrew@skamandros~$ mplayer -cache 1024 \
> mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma
MPlayer SVN-r29178-4.2.4 (C) 2000-2009 MPlayer Team

Playing mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma.
STREAM_ASF, URL: mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma
Resolving audability.wmsvc.vitalstreamcdn.com for AF_INET6...
Couldn't resolve name for AF_INET6: audability.wmsvc.vitalstreamcdn.com
Resolving audability.wmsvc.vitalstreamcdn.com for AF_INET...
Connecting to server audability.wmsvc.vitalstreamcdn.com[64.7.222.2]: 1755...
Connected
unknown object
unknown object
file object, packet length = 5493 (5493)
unknown object
unknown object
stream object, stream ID: 1
unknown object
data object
mmst packet_length = 5493
Cache size set to 1024 KBytes
Cache fill: 18.75% (196608 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: Audability Test Stream
 author: Audability
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
Everything done. Thank you for downloading a media file containing proprietary and patented technology.
A:  36.7 (36.6) of 37.0 (37.0)  0.3% 0% 

Exiting... (End of file)

```

All the best,

Andrew

---

### Post by dunbrokin on 2009-04-18
[http://audability.com/events/test-stream.asx](http://audability.com/events/test-stream.asx)

Maybe it is my systerm, but the above will not play for me.....

---

### Post by dunbrokin on 2009-04-18
> **dunbrokin said:**
> [http://audability.com/events/test-stream.asx](http://audability.com/events/test-stream.asx)

Maybe it is my systerm, but the above will not play for me.....

I lie...it did play for me.....eventually...

But how do I get to examine an asx file....this is all new to me ...sorry!

---

### Post by andrew.46 on 2009-04-18
Hi dunbrokin,

> **dunbrokin said:**
> I lie...it did play for me.....eventually...

But how do I get to examine an asx file....this is all new to me ...sorry!

Glad you got to hear it, although it was not that much after all :-). To analyse the asx file itself try:

```
cd Desktop
wget http://audability.com/events/test-stream.asx
```

Then open the file test-stream.asx with a text editor like gedit or whatever your preference is. Then you will see that an asx file is like a menu that simply tells the browser / media player what to do and where to go. 

Decent media players like MPlayer and vlc can read these instructions and find the stream. MPlayer has a -playlist option for this and vlc has something similar in the menus. Fascinating stuff isn't it :-).

All the best,

Andrew

**Edit:** Correction, vlc *used* to have an option called 'playlist' in the network menu. Played this stream ok with vlc 0.9.9

---

### Post by dunbrokin on 2009-04-18
<td colspan="2">Please click the button below to start the webcast.</td>
                                  </tr>
                                  <tr>
                                    <td colspan="2">&nbsp;</td>
                                  </tr>
                                <tr>

                                  <td colspan="2"><form name="form1" method="post" action="lobby.aspx?Event_ID=630" id="form1">
<div>
<input type="hidden" name="__VIEWSTATE" id="__VIEWSTATE" value="/wEPDwUKMjA0MjMxNTU1OGRkclKQhowpFYQDvvgoKB7K1P//sOo=" />
</div>

                                      <div id="goLive"> </div>
                                    </form></td>
                                  </tr>
                                  <tr>
                                    <td colspan="2">&nbsp;</td>

                                  </tr>
                                  <tr>
                                    <td colspan="2">&nbsp;</td>
                                  </tr>
                                  <!--<tr>
                                    <td colspan="2"><strong>Forward-Looking Statements:</strong></td>
                                </tr>
                                  <tr>
                                    <td colspan="2" height="1" bgcolor="#999999"></td>
                                </tr>
                                  <tr>
                                    <td colspan="2">&nbsp;</td>
                                  </tr>
                                  <tr>
                                    <td colspan="2"><p>TBD</p></td>
                                </tr> -->
                              </table></td>
                              <td valign="top" width="13">&nbsp;</td>
                            </tr>
                        </table></td>

                      </tr>
                    
                  </table></td>


I cannot seem to find a similar site relating to the webcast itself. :(

---

### Post by andrew.46 on 2009-04-18
Hi dunbrokin,

Unfortunately some detective work is required as for some reason people are keen to shield the bare address of such streams. This one is pretty easy though. Once you use the 'Click here to test your system' a new window should open up, stripped of the usual browser trappings. On Firefox smply press Ctrl+U and you then see the html source. Embedded in this source you will see: 

```
<script language='JavaScript'>videoms('**[COLOR="Red"]http://audability.com/events/test-stream.asx[/COLOR]**','full',320,0);</script>
```

and this is the asx playlist information. Takes a little getting used to but there are many, many tricks to finding stream addresses. It should not be necessary in the first place really...

Andrew

---

### Post by dunbrokin on 2009-04-19
> **andrew.46 said:**
> Hi dunbrokin,

Unfortunately some detective work is required as for some reason people are keen to shield the bare address of such streams. This one is pretty easy though. Once you use the 'Click here to test your system' a new window should open up, stripped of the usual browser trappings. On Firefox smply press Ctrl+U and you then see the html source. Embedded in this source you will see: 

```
<script language='JavaScript'>videoms('**[COLOR="Red"]http://audability.com/events/test-stream.asx[/COLOR]**','full',320,0);</script>
```

and this is the asx playlist information. Takes a little getting used to but there are many, many tricks to finding stream addresses. It should not be necessary in the first place really...

Andrew

Thanks for that....yes I can see how it works on the test stream....but I cannot find any information on the webcast itself which would enable me to do the smae as you have done for the test.....what am I missing?

---

### Post by andrew.46 on 2009-04-19
Hi dunbroken,

> **dunbrokin said:**
> Thanks for that....yes I can see how it works on the test stream....but I cannot find any information on the webcast itself which would enable me to do the smae as you have done for the test.....what am I missing?

The address is the html, the .asx one, is the file you need to download and the best way is to use wget is a terminal window:

```
wget http://audability.com/events/test-stream.asx
```

and this contains the stream information.

All the best,

Andrew

---

### Post by dunbrokin on 2009-04-19
OK this is where I have the problem...

The Launch Website page is [http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/lobby.aspx?Event_ID=630](http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/lobby.aspx?Event_ID=630)

now if I wget that...then this is what I get.

~$ wget [http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/primary.aspx?Event_ID=630](http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/primary.aspx?Event_ID=630)
--2009-04-19 19:18:28--  [http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/primary.aspx?Event_ID=630](http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/primary.aspx?Event_ID=630)
Resolving audability.com... 207.5.77.188
Connecting to audability.com|207.5.77.188|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 861 [text/html]
Saving to: `primary.aspx?Event_ID=630'

100%[======================================>] 861         --.-K/s   in 0s      

2009-04-19 19:18:28 (41.7 MB/s) - `primary.aspx?Event_ID=630' saved [861/861]

What does this tell me?

---

### Post by andrew.46 on 2009-04-19
Hi dunbrokin,

> **dunbrokin said:**
> 

```
$ wget http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/primary.aspx?Event_ID=630
```

[...]

What does this tell me?

Unfortunately it tells you that you have downloaded the wrong page :-). You are after the next one, the one that follows when you press on the link 'Click here to test your system'.

All the best,

Andrew

---

### Post by dunbrokin on 2009-04-19
> **andrew.46 said:**
> Hi dunbrokin,



Unfortunately it tells you that you have downloaded the wrong page :-). You are after the next one, the one that follows when you press on the link 'Click here to test your system'.

All the best,

Andrew

I get the same result from both pages....!!!

---

### Post by dunbrokin on 2009-04-21
bump

---

### Post by andrew.46 on 2009-04-21
Hi again Dunbrokin!!

My apologies I had to spend some time in the big blue room  :-). So perhaps to recapitulate:

MPlayer and vlc can both quite happily play this stream as follows:

```

mplayer mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma

cvlc mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma
```

These are the commandline versions of both programs, the gui version of both also work with this stream address.

Some detective work is required to isolate this address, although I note that the MPlayer plugin plays the stream quite well from within Firefox. So to find the stream address first go to:

[http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/registrationform.aspx?Event_ID=630](http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/registrationform.aspx?Event_ID=630)

and then click on the link that says: 'Click here to test your system'. This opens up another page that is craftily bereft of the normal browser options:

[http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/test.aspx](http://audability.com/AudabilityAdmin/Clients/GlobalPayments/10630_1015200880000AM/test.aspx)

Now you may very well be happy to allow the MPlayer plugin or something similar play the sound for you. However while you are on this page press Ctrl +U and you will see in the page source the following:

```

<script language='JavaScript'>videoms('**[COLOR="Red"]http://audability.com/events/test-stream.asx[/COLOR]**','full',320,0);</script>

```

Now since we know that an asx file is an 'Advanced Stream Redirector' we can suspect that there may be a few URLs embedded within it. So to download this asx file we can use wget:

```

 wget http://audability.com/events/test-stream.asx

```

and then open the file test-stream.asx with a text editor:

```

<asx version = "3.0">
   <title>Webcast System Test</title>
   <author>Audability</author>
   <copyright>Audability</copyright>
   <entry>
      <title>Webcast System Test</title>
      <Author>Audability</Author>
      <copyright>Audability</copyright>
	  <ref href = "rtsp://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma"/>
          <ref href = "mms://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma"/>
	  <ref href = "http://audability.wmsvc.vitalstreamcdn.com/audability_vitalstream_com/test-stream.wma"/>
   </entry>
</asx>

```

And of these 3 protocols the only one I could get to work is the mms one :-). Hopefully this is a little clearer?

Andrew

---

### Post by dunbrokin on 2009-04-21
Thanks ....that is very clear. However, that only plays the test....it does not play the webcast. How do I move from what you have shown me here - for which I am very grateful - to playing the full podcast. My brain is missing a link.....

---

### Post by andrew.46 on 2009-04-21
Hi dunbrokin,

> **dunbrokin said:**
> Thanks ....that is very clear. However, that only plays the test....it does not play the webcast. How do I move from what you have shown me here - for which I am very grateful - to playing the full podcast. My brain is missing a link.....

The penny drops for me, I assumed you were having trouble playing the test :-). As far as I can see there is no other broadcast available on this page. Presumable you need to 'register' as per the first page? My apologies for not understanding your question!

Andrew

---

### Post by dunbrokin on 2009-04-21
Yes, thanks, I need to play the webcast, I have registered (you can easily do so with fictitious information) and tried to play the webcast or tried to get information in the way that you have shown....but, so far, have achieved nothing.

---

### Post by andrew.46 on 2009-04-21
Hu dunbrokin,

> **dunbrokin said:**
> Yes, thanks, I need to play the webcast, I have registered (you can easily do so with fictitious information) and tried to play the webcast or tried to get information in the way that you have shown....but, so far, have achieved nothing.

Hmmm... I did the same but a mysterious plugin was required. I am no further help to you I am afraid. Hopefully somebody clever can unravel this one?

All the best,

Andrew

---

### Post by dunbrokin on 2009-04-21
> **andrew.46 said:**
> Hu dunbrokin,



Hmmm... I did the same but a mysterious plugin was required. I am no further help to you I am afraid. Hopefully somebody clever can unravel this one?

All the best,

Andrew

I have tried everything....in the end I had to go to windows and to IE and to the latest MS Media player.....

---

