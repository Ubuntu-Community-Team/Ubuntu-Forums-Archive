---
title: "Show me how to play Mythweb .asx on win7"
date: 2012-06-04
forum: Mythbuntu
---

### Post by nhtrader on 2012-06-04
PC1:mythtbuntu 12.04, Mythtv 0.25+fixes FE/BE on same pc 
PC2:Win7 HP SP1 64bit, IE9, Opera 11.64, WMP 12.0.7601, WMC 6.1.7601

I am using a webbrowser (IE9, or Opera11.64) on Win7 to access Mythweb.

I've verified file associations for WMP and asx is active.I've checked MIME type associations in both browsers for .asx and they both point to WMP. But when I select a recorded TV program using asx I get an error message: Windows does not support this file.

What am I missing? Isn't asx a windows video format? Why doesn't asx from Mythweb play on win7?

---

### Post by nickrout on 2012-06-04
> **nhtrader said:**
> PC1:mythtbuntu 12.04, Mythtv 0.25+fixes FE/BE on same pc 
PC2:Win7 HP SP1 64bit, IE9, Opera 11.64, WMP 12.0.7601, WMC 6.1.7601

I am using a webbrowser (IE9, or Opera11.64) on Win7 to access Mythweb.

I've verified file associations for WMP and asx is active.I've checked MIME type associations in both browsers for .asx and they both point to WMP. But when I select a recorded TV program using asx I get an error message: Windows does not support this file.

What am I missing? Isn't asx a windows video format? Why doesn't asx from Mythweb play on win7?

codec or container issue perhaps?

if you download the file to the windows machine and then play it directly in WMP does it work?

---

### Post by nhtrader on 2012-06-04
> **nickrout said:**
> codec or container issue perhaps?

if you download the file to the windows machine and then play it directly in WMP does it work?


To answer your question, my win7 PC can play all of the .mpg videos in DIR /recordings if I use my win7 PC to connect to the mythbox via the Network. I double click a .mpg and it plays with WMP.

But when I use mythweb to access ASX Here's the XML file that gets saved:
<ASX version = "3.0">
<TITLE>Some TV SHOW I REcorded</TITLE>
<ENTRY>
<TITLE>Some TV SHOW I REcorded - </TITLE>
<AUTHOR>MythTV - MythWeb</AUTHOR>
<COPYRIGHT>GPL</COPYRIGHT>
<REF HREF = "http://10.10.10.12:80//mythweb/pl/stream/3111/1338597000" />
</ENTRY>
</ASX>

The point being, I thought that the ASX option was to enable users to view the show on the fly and not wait for it to download before we can watch it. Secondly, I thought ASX was a format that Windows understands. 

I'm guessing that b/c the file extension is missing in the XML Windows doesn't know what to do. But I'm just guessing.

---

### Post by azmyth on 2012-06-04
Try installing VLC for windows 7 and using this for your asx streams.

Also what kind of tuner card do you have?

---

### Post by nhtrader on 2012-06-04
> **azmyth said:**
> Try installing VLC for windows 7 and using this for your asx streams.

Also what kind of tuner card do you have?

Thank you for this suggestion. BTW, VLC works just fine. But I'm not interested in a work around. 

I'm interested in specifically learning about how the ASX stream works. I've tried to use this since v0.23 and I still don't understand how it works. 

My experience has always been to use a "work around" but now I'm interested in getting this to work. And by "work"; I mean "click & play". I shouldn't need to use VLC or any other media player. ASX is specifically a windows video format and therefore I would assume that a windows based PC should be able to view the video.

---

### Post by nickrout on 2012-06-04
What happens when you enter that url ([http://10.10.10.12:80//mythweb/pl/stream/3111/1338597000](http://10.10.10.12:80//mythweb/pl/stream/3111/1338597000)) into wmp?

---

### Post by nhtrader on 2012-06-04
> **nickrout said:**
> What happens when you enter that url ([http://10.10.10.12:80//mythweb/pl/stream/3111/1338597000](http://10.10.10.12:80//mythweb/pl/stream/3111/1338597000)) into wmp?

1. No playback. 
2. The error message appears Windows does not support this format.


BTW, this URL doesn't really exist. It's a virtual address - right? Meaning there is no physical DIR that contains ./mythweb/pl/stream nor does there exist a physical file.

I'm assuming that this should be a symbol link to the actual *.mpg.

Is this a correct depiction of the process?

---

### Post by tgm4883 on 2012-06-04
> **nhtrader said:**
> 1. No playback. 
2. The error message appears Windows does not support this format.


BTW, this URL doesn't really exist. It's a virtual address - right? Meaning there is no physical DIR that contains ./mythweb/pl/stream nor does there exist a physical file.

I'm assuming that this should be a symbol link to the actual *.mpg.

Is this a correct depiction of the process?

What happens if you put the following URL into WMP? (Notice the .asx I added to the end and the no double slashes

```
http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.asx
```

---

### Post by nhtrader on 2012-06-04
> **tgm4883 said:**
> What happens if you put the following URL into WMP? (Notice the .asx I added to the end and the no double slashes

```
http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.asx
```


I tried the following: (for the heck of it, I tried some other ext's)
[http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.asx](http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.asx)
[http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000](http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000)
[http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.asf](http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.asf)
[http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.mpg](http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000.mpg)

All 4 urls had the same response.
1.No playback.
2.Same error msg

---

### Post by nickrout on 2012-06-04
> **nhtrader said:**
> Thank you for this suggestion. BTW, VLC works just fine. But I'm not interested in a work around. why not? vlc is a far superior player to WMP

---

### Post by nhtrader on 2012-06-04
> **nickrout said:**
> why not? vlc is a far superior player to WMP

The point is that mythweb generates a webpage that offers us users a supposedly easy windows streaming option. But I can't get to work. In addition, I've never seen this "ASX" link work. So why it is here?

Secondly, the point of having a home website (mythweb) is to facilitate easy remote access. It is suppose to be "click & play" and not, well, you need to click/debug(find out what works)/install more software to see the recordings.


If you could explain how mythweb gets the browser-client from:

[http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000](http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000)

to the actual recording:

/var/lib/mythtv/recordings/3111_20120601203000.mpg

That would be helpful.

Lastly, is the ASX link suppose to be "click & play" or not? No one yet has acknowledged that this is indeed what this Button is for.

---

### Post by nickrout on 2012-06-04
> **nhtrader said:**
> 

[http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000](http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000)

to the actual recording:

/var/lib/mythtv/recordings/3111_20120601203000.mpg

That would be helpful.read the code, it's open source. perl is not the easiest to understand, nor the hardest.> 

Lastly, is the ASX link suppose to be "click & play" or not? No one yet has acknowledged that this is indeed what this Button is for.

yes, and according to you it is, if you use a decent media player.

Otherwise I suggest the mailing list where I have seen this discussed many times. Or search it's archives at [http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

---

### Post by tgm4883 on 2012-06-04
> **nhtrader said:**
> The point is that mythweb generates a webpage that offers us users a supposedly easy windows streaming option. But I can't get to work. In addition, I've never seen this "ASX" link work. So why it is here?

Secondly, the point of having a home website (mythweb) is to facilitate easy remote access. It is suppose to be "click & play" and not, well, you need to click/debug(find out what works)/install more software to see the recordings.


If you could explain how mythweb gets the browser-client from:

[http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000](http://10.10.10.12:80/mythweb/pl/stream/3111/1338597000)

to the actual recording:

/var/lib/mythtv/recordings/3111_20120601203000.mpg

That would be helpful.

Lastly, is the ASX link suppose to be "click & play" or not? No one yet has acknowledged that this is indeed what this Button is for.

The ASX file format is basically just an XML playlist. Being that WMP is reporting that it doesn't support the file, but VLC and totem play it back just fine it sounds to me like an issue with WMP. Looking at past Microsoft products, WMP isn't the first to be finicky about the files it plays back.

---

### Post by nhtrader on 2012-06-04
> **tgm4883 said:**
> The ASX file format is basically just an XML playlist. Being that WMP is reporting that it doesn't support the file, but VLC and totem play it back just fine it sounds to me like an issue with WMP. Looking at past Microsoft products, WMP isn't the first to be finicky about the files it plays back.

In an effort to provide more information, I found what I hope will be additional useful information from the apache logs: /var/log/apache2/access.log

Note that when I use IE9, it strictly choses WMP. No dropdown box appears to give me more choices. 
Whereas, Opera, provides a dropdown box with several choices.
Below you will see the HTTP requests as recorded in the log:

```

These are the HTTP requests from my Win7 PC using IE9 as the webbrowser:

10.10.10.13 - - [04/Jun/2012:23:43:23 -0400] "GET /mythweb/ HTTP/1.1" 200 2996 "-" "Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Win64; x64; Trident/5.0; MAAU)"
10.10.10.13 - - [04/Jun/2012:23:43:25 -0400] "GET /mythweb/tv/recorded HTTP/1.1" 200 7383 "http://10.10.10.12/mythweb/" "Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Win64; x64; Trident/5.0; MAAU)"
10.10.10.13 - - [04/Jun/2012:23:43:31 -0400] "GET //mythweb/pl/stream/3111/1338597000.asx HTTP/1.1" 200 548 "http://10.10.10.12/mythweb/tv/recorded" "Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Win64; x64; Trident/5.0; MAAU)"
10.10.10.13 - - [04/Jun/2012:23:43:39 -0400] "GET /mythweb/pl/stream/3111/1338597000 HTTP/1.1" 200 81760 "-" "Windows-Media-Player/12.0.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:43:39 -0400] "GET /mythweb/pl/stream/3111/1338597000 HTTP/1.1" 206 595216 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:43:39 -0400] "GET /mythweb/pl/stream/3111/1338597000 HTTP/1.1" 200 80300 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:43:40 -0400] "GET /mythweb/pl/stream/3111/1338597000 HTTP/1.1" 200 52560 "-" "NSPlayer/12.0.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:43:40 -0400] "GET /mythweb/pl/stream/3111/1338597000 HTTP/1.1" 200 99280 "-" "NSPlayer/12.0.7601.17514 WMFSDK/12.0"
10.10.10.13 - - [04/Jun/2012:23:43:40 -0400] "GET /mythweb/pl/stream/3111/1338597000 HTTP/1.1" 206 1037572 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"




These are the HTTP requests from my Win7 PC using Opera as the webbrowser:
The following requests resulted from me selected WMPlayer as the program:
10.10.10.13 - - [04/Jun/2012:23:24:43 -0400] "GET //mythweb/pl/stream/3041/1338595200.asx HTTP/1.1" 200 527 "http://10.10.10.12/mythweb/tv/recorded" "Opera/9.80 (Windows NT 6.1; WOW64; U; en) Presto/2.10.229 Version/11.64"
10.10.10.13 - - [04/Jun/2012:23:25:03 -0400] "GET /mythweb/pl/stream/3041/1338595200 HTTP/1.1" 200 87600 "-" "Windows-Media-Player/12.0.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:25:03 -0400] "GET /mythweb/pl/stream/3041/1338595200 HTTP/1.1" 200 656799 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:25:03 -0400] "GET /mythweb/pl/stream/3041/1338595200 HTTP/1.1" 200 174323 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:25:03 -0400] "GET /mythweb/pl/stream/3041/1338595200 HTTP/1.1" 200 49640 "-" "NSPlayer/12.0.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:25:03 -0400] "GET /mythweb/pl/stream/3041/1338595200 HTTP/1.1" 200 110960 "-" "NSPlayer/12.0.7601.17514 WMFSDK/12.0"
10.10.10.13 - - [04/Jun/2012:23:25:04 -0400] "GET /mythweb/pl/stream/3041/1338595200 HTTP/1.1" 206 761451 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"

The following requests resulted from me selected WMCenter as the program:
10.10.10.13 - - [04/Jun/2012:23:26:04 -0400] "GET //mythweb/pl/stream/3561/1338528600.asx HTTP/1.1" 200 581 "http://10.10.10.12/mythweb/tv/recorded" "Opera/9.80 (Windows NT 6.1; WOW64; U; en) Presto/2.10.229 Version/11.64"
10.10.10.13 - - [04/Jun/2012:23:26:19 -0400] "GET /mythweb/pl/stream/3561/1338528600 HTTP/1.1" 200 62780 "-" "Windows-Media-Player/12.0.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:26:19 -0400] "GET /mythweb/pl/stream/3561/1338528600 HTTP/1.1" 200 617376 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:26:19 -0400] "GET /mythweb/pl/stream/3561/1338528600 HTTP/1.1" 200 167028 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:26:19 -0400] "GET /mythweb/pl/stream/3561/1338528600 HTTP/1.1" 200 49640 "-" "NSPlayer/12.0.7601.17514"
10.10.10.13 - - [04/Jun/2012:23:26:19 -0400] "GET /mythweb/pl/stream/3561/1338528600 HTTP/1.1" 200 105120 "-" "NSPlayer/12.0.7601.17514 WMFSDK/12.0"
10.10.10.13 - - [04/Jun/2012:23:26:20 -0400] "GET /mythweb/pl/stream/3561/1338528600 HTTP/1.1" 206 275866 "-" "NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514"

The following requests resulted from me selected VLC as the program: (note this was the only program of the three that played the video)
10.10.10.13 - - [04/Jun/2012:23:27:06 -0400] "GET //mythweb/pl/stream/3251/1338595200.asx HTTP/1.1" 200 497 "http://10.10.10.12/mythweb/tv/recorded" "Opera/9.80 (Windows NT 6.1; WOW64; U; en) Presto/2.10.229 Version/11.64"
10.10.10.13 - - [04/Jun/2012:23:27:14 -0400] "GET //mythweb/pl/stream/3251/1338595200 HTTP/1.1" 206 2379119 "-" "VLC/2.0.1 LibVLC/2.0.1"

```

---

### Post by nickrout on 2012-06-05
All of which goes to show that windows players appear to do the wrong thing and vlc does the right thing.

I am no expert in these matters, but the following is what it appears to me is happening:

Windows and MS written programs rely heavily on file extensions (eg .mpg) whereas much open source and linux software relies more on mime headers and/or the contents of the file (see eg /etc/gnome-vfs-mime-magic). I suspect WMP is looking for a file extension and crapping out when it doesn't find one. VLC is looking at the mime type (or perhaps the file content) and determining that it is video/mpeg.

FWIW wget shows me that the asx file has mime type video/x-ms-asf (correct) and the url it points to has mimetype video/mpeg (again appears correct).

My conclusion: WMP and it's allies get it wrong!

---

### Post by nhtrader on 2012-06-05
> **nickrout said:**
> All of which goes to show that windows players appear to do the wrong thing and vlc does the right thing.


1. Your expression of right and wrong is curious. However, I'm still interested in learning if this "ASX" feature/function of mythweb is working or not.

2. Is the URL that mythweb's php code generates correct? (is the use of, and/or occurrence, of the double-slash correct?) (no one yet has explained how the mythweb ASX generated URL points to the actual video's location)

3. Was this feature/function added for the benefit of windows users?

4. Is this "ASX" feature/function suppose to be "click & play"?

5. What is the merit of mythweb having this "ASX" link?

---

### Post by tgm4883 on 2012-06-05
> **nhtrader said:**
> 1. Your expression of right and wrong is curious. However, I'm still interested in learning if this "ASX" feature/function of mythweb is working or not.


Works for me, although I don't have WMP to test. I asked someone in the mythtv users channel to test and they said it works for them on windows 7 with WMP. His comments are below.


> after i mounted my recordings, and got the necessary perl reqs, it works fine here
0.25 (technically master), and win7 with WMP
these are mpeg2 recordings off an HDHR by the way
in all those examples, he chose a different recording
perhaps those other recordings are orphaned and dont actually exist?


> **nhtrader said:**
> 
2. Is the URL that mythweb's php code generates correct? (is the use of, and/or occurrence, of the double-slash correct?) (no one yet has explained how the mythweb ASX generated URL points to the actual video's location)


A mythtv developer has told me that the information inside the ASX file you provided was correct. It uses /var/www/mythweb/mythweb.pl to point to the right link. 

> **nhtrader said:**
> 
3. Was this feature/function added for the benefit of windows users?


Yes/No. This feature was added as a benefit to both Linux and Windows users. See [http://code.mythtv.org/trac/ticket/2660](http://code.mythtv.org/trac/ticket/2660)

> **nhtrader said:**
> 
4. Is this "ASX" feature/function suppose to be "click & play"?


Yes

> **nhtrader said:**
> 
5. What is the merit of mythweb having this "ASX" link?

It allows

---

### Post by nickrout on 2012-06-05
> **nhtrader said:**
> 1. Your expression of right and wrong is curious.  how so when vlc works and (at least for you) WMP doesn't> However, I'm still interested in learning if this "ASX" feature/function of mythweb is working or not.short answer: yes> 

2. Is the URL that mythweb's php code generates correct? (is the use of, and/or occurrence, of the double-slash correct?) (no one yet has explained how the mythweb ASX generated URL points to the actual video's location)As in any url repeated slashes do not matter, as some testing will reveal:

```
nick@dell:~$ wget http://media:80////////mythweb/pl/stream/2003/1338875940
--2012-06-06 08:02:53--  http://media////////mythweb/pl/stream/2003/1338875940
Resolving media... 192.168.1.11
Connecting to media|192.168.1.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5586551036 (5.2G) [video/mpeg]
Saving to: `1338875940'

```

See? > 
3. Was this feature/function added for the benefit of windows users?

4. Is this "ASX" feature/function suppose to be "click & play"?

5. What is the merit of mythweb having this "ASX" link?

Actually I have the same result as Thomas' correspondent, works on WMP on Win7 for me, albeit from Firefox (IE being verbotten to me, although it exists on the system I used and I'll give it a try sometime).

---

### Post by nhtrader on 2012-06-05
Thank you for verifying functionality. I'm glad it works.


Now, is there any other means to help in diagnosing why none of my 4 Windows based PCs can view a recording served up by mythweb using "ASX" on my home network?

---

### Post by nickrout on 2012-06-05
But you said it does work with VLC.

Have you searched the mailing list archives or asked there? See my post #12 above.

---

### Post by nhtrader on 2012-06-05
> **nickrout said:**
> But you said it does work with VLC.

Have you searched the mailing list archives or asked there? See my post #12 above.

Yes, it does work with VLC.

But you gave me an idea as to how to diagnose my Win7 inability to play the video. I just downloaded a windows version WGET and used it to fetch the video and tried to play it. 

So on my win7 PC, it will not play the movie 123456789 directly, but it will play 123456789.asf immediately. Great news; sort of.

What's interesting is that my Win7 doesn't offer any options to handle it. Meaning when I right-click this unknown file, all I have is the option to "OPEN". When I select this "OPEN" option, and then select WMP as the application to use it, then I get this prompt:

The selected file has an extension (.) that is not recognized by Windows Media Player, but the Player may still be able to play it. Because the extension is unknown by the Player you should be sure that the file comes from a trustworthy source. Do you want the Player to Play this content?

Select YES. Then it plays.

There in lies the problem. No additional codecs are necessary. No additional software is necessary. All I need is an extension added to the filename. Therefore, Mythweb works sort of with windows. It is serving up a usable video file that is compatible with WMP and WMC, but due to stricter security rules, windows is refusing to play an unknown format. The syntax is ambiguous and therefore it refuses to play the stream. 

So I found one php script that creates the ASX XML webpage served to a client: /usr/share/mythtv/mythweb/modules/stream/stream_asx.pl 

Modifying this script would enable me to change the extension from "" to ".asf", but this doesn't solve the problem. It alone won't work b/c the ASX XML contents will tell the client (Win7 IE) to look for an .asf file which doesn't exist. Of course the original file does exist but it doesn't have the .asf extension yet. So I would need to find the script that is responsible for creating the original filename to that I can modify it to add the extension ".asf" After that I'm hoping that the ASX feature will then truly be "click & play" on all 4 Win7 PCs.

Does anyone know which php script does this?

I will now look into this one: /var/www/mythweb/mythweb.pl

---

### Post by nickrout on 2012-06-05
So are you saying simply by renaming the file with an extension WMP recognises, it will play? (Actually you should probably name it to .mpg, not .asf, it's not an asf stream it is an mpeg-ts stream)

Try the mailing list. (That's the third time I have said that). You are likely to find someone there to help, probably even the author of the mythweb code.


However it is windows corporation you should file a bug with. mythweb delivers a valid mpeg stream with a valid mime type, file extension should not matter - and indeed with firefox WMP does the right thing.

If you are looking at the mythweb code, doing this found some references:

```
cd/usr/share/mythtv/mythweb
 grep asx * -r --exclude-dir=data -C10
```

Gives you all the hits of the string asx in the source code, with 10 lines of context either side. I am no expert in the code myself, and I see no breakage on my systems so I am not going to analyse it further. Good luck.

---

### Post by nhtrader on 2012-06-05
That's basically how I found the stream_asx.pl script.

But I think I've hit a dead end.

1. I changed the code in stream_asx.pl to add the extension .asf.
2. I used Win7 IE to fetch the tv program, and it failed.
3. Then I tried using wget on the Win7 PC to fetch 1234567898.asf and wget downloaded it. 
4. Then I used wget again to fetch 123456789 (without extension .asf) and it downloaded that too. This was unexpected b/c I was expecting an HTTP 404 error - file not found. So this doesn't add any clarity or help in diagnosing the problem.
There shouldn't be two instances of this recording; only one = recording.asf

I was sure this was going to get me closer to the solution. Now I'll have to wait for an expert to guide me through this.

Here are the access.log entries which show that mythweb served up both files:
10.10.10.13 - - [05/Jun/2012:21:14:57 -0400] "GET //mythweb/pl/stream/3111/1338597000.asf HTTP/1.0" 200 710088765 "-" "Wget/1.9"
10.10.10.13 - - [05/Jun/2012:21:21:39 -0400] "GET //mythweb/pl/stream/3111/1338597000 HTTP/1.0" 200 710088765 "-" "Wget/1.9"

---

### Post by nickrout on 2012-06-05
why asf? see my previous post.

---

### Post by nickrout on 2012-06-05
Actually following your post I noted that you can add any extension to the download url and it will add it to the file.

Try changing your code to add .mpg not .asf to the url - if WMP is recognising the stream type via the extension then it's important to get it right. These are mpeg-ts streams, not asf.

---

### Post by nhtrader on 2012-06-05
> **nickrout said:**
> Actually following your post I noted that you can add any extension to the download url and it will add it to the file.

Try changing your code to add .mpg not .asf to the url - if WMP is recognising the stream type via the extension then it's important to get it right. These are mpeg-ts streams, not asf.

Yes. The ...stream_asx.pl  does indeed change the extension. Since then I learned that mythweb serves up any extenstion you want without changing the script. Try it. Just use wget to fetch a recording and add any extension you like ( mpg, asf, rtx, qwert...) and wget will fetch it. No script change required.

The thing I learned tonight is that on the Win7 PC, it will play the wget fetched files (local copy of recording with any extension: mpg, asf, joe). But if I use WMP's OPEN URL function and try to play the recording directly over the network. WMP fails. It doesn't matter what the extension is.

So in summary, there are 3 ways to access this recording on Win7:
1. access a local copy of the recording (this works)
(next 2 ways are via the network)
2. Through WMP's Open URL Menu Option: ../pl/stream/3111/1234567.mpg, or asf (this fails and that's why ASX is not working for me.)
3. Through the home network discovery (actual file location) //MYTHBOX:/recordings/tv_show.mpg (this works)


Lastly, I wanted to add the following information. Here are the codecs that are installed and in use by WMP
```

Audio Codecs
Type	Name	Format	Binary	Version
ACM	Microsoft IMA ADPCM CODEC	0011	imaadp32.acm	6.1.7600.16385
ACM	Microsoft CCITT G.711 A-Law and u-Law CODEC	0007	msg711.acm	6.1.7600.16385
ACM	Microsoft GSM 6.10 Audio CODEC	0031	msgsm32.acm	6.1.7600.16385
ACM	Microsoft ADPCM CODEC	0002	msadp32.acm	6.1.7600.16385
ACM	Fraunhofer IIS MPEG Layer-3 Codec (decode only)	0055	l3codeca.acm	1.9.0.401
ACM	Messenger Audio Codec	028E	sirenacm.dll	14.0.8050.1202
ACM	Microsoft PCM Converter	0001		
DMO	WMAudio Decoder DMO	0160, 0161, 0162, 0163	WMADMOD.DLL	6.1.7601.17514
DMO	WMAPro over S/PDIF DMO	0162	WMADMOD.DLL	6.1.7601.17514
DMO	WMSpeech Decoder DMO	000A, 000B	WMSPDMOD.DLL	6.1.7601.17514
DMO	MP3 Decoder DMO	0055	mp3dmod.dll	6.1.7600.16385

Video Codecs
Type	Name	Format	Binary	Version
ICM	Microsoft RLE	MRLE	msrle32.dll	6.1.7601.17514
ICM	Microsoft Video 1	MSVC	msvidc32.dll	6.1.7601.17514
ICM	Microsoft YUV	UYVY	msyuv.dll	6.1.7601.17514
ICM	Intel IYUV codec	IYUV	iyuv_32.dll	6.1.7601.17514
ICM	Toshiba YUV Codec	Y411	tsbyuv.dll	6.1.7601.17514
ICM	Cinepak Codec by Radius	cvid	iccvid.dll	1.10.0.13
DMO	Mpeg4s Decoder DMO	mp4s, MP4S, m4s2, M4S2, MP4V, mp4v, XVID, xvid, DIVX, DX50	mp4sdecd.dll	6.1.7600.16385
DMO	WMV Screen decoder DMO	MSS1, MSS2	wmvsdecd.dll	6.1.7601.17514
DMO	WMVideo Decoder DMO	WMV1, WMV2, WMV3, WMVA, WVC1, WMVP, WVP2	wmvdecod.dll	6.1.7601.17514
DMO	Mpeg43 Decoder DMO	mp43, MP43	mp43decd.dll	6.1.7600.16385
DMO	Mpeg4 Decoder DMO	MPG4, mpg4, mp42, MP42	mpg4decd.dll	6.1.7600.1638

```

---

### Post by nickrout on 2012-06-06
> **nhtrader said:**
> Yes. The ...stream_asx.pl  does indeed change the extension. Since then I learned that mythweb serves up any extenstion you want without changing the script. Try it. Just use wget to fetch a recording and add any extension you like ( mpg, asf, rtx, qwert...) and wget will fetch it. No script change required.

The thing I learned tonight is that on the Win7 PC, it will play the wget fetched files (local copy of recording with any extension: mpg, asf, joe). But if I use WMP's OPEN URL function and try to play the recording directly over the network. WMP fails. It doesn't matter what the extension is.

So in summary, there are 3 ways to access this recording on Win7:
1. access a local copy of the recording (this works)
(next 2 ways are via the network)
2. Through WMP's Open URL Menu Option: ../pl/stream/3111/1234567.mpg, or asf (this fails and that's why ASX is not working for me.)
3. Through the home network discovery (actual file location) //MYTHBOX:/recordings/tv_show.mpg (this works)



Or of course by installing mythtv :)

---

### Post by tgm4883 on 2012-06-06
> **nickrout said:**
> Or of course by installing mythtv :)

Or by using VLC. :)


Out of curiosity, does it work correctly if you use Firefox in Windows 7? Maybe it's an IE issue.

---

### Post by nhtrader on 2012-06-06
> **tgm4883 said:**
> Or by using VLC. :)


Out of curiosity, does it work correctly if you use Firefox in Windows 7? Maybe it's an IE issue.

For you I did a fresh install on Win7 of FF 13.0.

1. I tried ASX feature and playback failed. The same message appeared.
2. then I installed the windows-firefox-plugin (b/c it is suppose to help with playback of windows media formats)
3. Again, the ASX feature failed to playback the video. The same message appeared. 


In an effort to delve into this more deeply. I downloaded and installed the wireshark pkg on mythbox. Set it up and got the following headers:

NOTE: I tried several methods. For comparison the HTTP headers for both the Direct Download and the ASX streaming mode are shown for the same TV show. Developers viewing these headers may notice that I modified mythweb's URL. I added the extension .asf and removed one of the slashes from the "double-slash". I did this to rule out any doubt that the URL was problematic for IE9. (it didn't make a difference. I still can't use ASX as "click & play")


```

===================================
Method - Win7 IE9 Direct Download of TVshow
=============================================

GET //mythweb/pl/stream/3111/1338597000 HTTP/1.1
Accept: text/html, application/xhtml+xml, */*
Referer: http://192.168.0.8/mythweb/tv/recorded
Accept-Language: en-US
User-Agent: Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Win64; x64; Trident/5.0; MAAU)
UA-CPU: AMD64
Accept-Encoding: gzip, deflate
Host: 192.168.0.8
Connection: Keep-Alive
Cookie: mythweb_id=2tqq5l1secmt6rg18h2u6fcts0

HTTP/1.1 200 OK
Date: Wed, 06 Jun 2012 19:30:18 GMT
Server: Apache/2.2.22 (Ubuntu)
Accept-ranges: bytes
Content-disposition: attachment; filename="Antiques Roadshow - UK.mpg"
Content-length: 710088408
Last-Modified: Sat, 02 Jun 2012 01:01:00 GMT
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/mpeg; charset=ISO-8859-1



===================================================
Method - Win7 IE9 ASX stream of TVshow
===============================================

GET //mythweb/pl/stream/3111/1338597000.asx HTTP/1.1
Accept: text/html, application/xhtml+xml, */*
Referer: http://192.168.0.8/mythweb/tv/recorded
Accept-Language: en-US
User-Agent: Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Win64; x64; Trident/5.0; MAAU)
UA-CPU: AMD64
Accept-Encoding: gzip, deflate
Host: 192.168.0.8
Connection: Keep-Alive
Cookie: mythweb_id=2tqq5l1secmt6rg18h2u6fcts0

HTTP/1.1 200 OK
Date: Wed, 06 Jun 2012 19:41:19 GMT
Server: Apache/2.2.22 (Ubuntu)
Content-disposition: attachment; filename="Antiques Roadshow - UK-.asx"
Content-length: 264
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/x-ms-asf; charset=ISO-8859-1

<ASX version = "3.0">
<TITLE>Antiques Roadshow - UK</TITLE>
<ENTRY>
<TITLE>Antiques Roadshow - UK - </TITLE>
<AUTHOR>MythTV - MythWeb</AUTHOR>
<COPYRIGHT>GPL</COPYRIGHT>
<REF HREF = "http://192.168.0.8:80//mythweb/pl/stream/3111/1338597000.asf" />
</ENTRY>
</ASX>

----------------------------------

GET /mythweb/pl/stream/3111/1338597000.asf HTTP/1.1
Cache-Control: no-cache
Connection: Keep-Alive
Pragma: getIfoFileURI.dlna.org
Accept: */*
If-Unmodified-Since: Sat, 02 Jun 2012 01:01:00 GMT
Range: bytes=40067072-710088407
User-Agent: NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514
GetContentFeatures.DLNA.ORG: 1
Host: 192.168.0.8

HTTP/1.1 206 Partial Content
Date: Wed, 06 Jun 2012 19:55:04 GMT
Server: Apache/2.2.22 (Ubuntu)
Accept-ranges: bytes
Content-disposition: attachment; filename="Antiques Roadshow - UK.mpg"
Content-length: 670021336
Content-range: bytes 40067072-710088407/710088408
Last-Modified: Sat, 02 Jun 2012 01:01:00 GMT
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/mpeg; charset=ISO-8859-1

------------------------------------------------------------
After a bunch of packets get passed along, this event occurs:
TCP  -  HTTP RST
then another GET request comes in from Win7
-------------------------------------------------------------

GET /mythweb/pl/stream/3111/1338597000.asf HTTP/1.1
Accept: */*
User-Agent: NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514
Icy-Metadata: 1
Accept-Encoding: gzip, deflate
Host: 192.168.0.8
Connection: Keep-Alive

HTTP/1.1 200 OK
Date: Wed, 06 Jun 2012 19:55:04 GMT
Server: Apache/2.2.22 (Ubuntu)
Accept-ranges: bytes
Content-disposition: attachment; filename="Antiques Roadshow - UK.mpg"
Content-length: 710088408
Last-Modified: Sat, 02 Jun 2012 01:01:00 GMT
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/mpeg; charset=ISO-8859-1

------------------------------------------------------------
After a bunch of packets get passed along, this event occurs:
TCP  -  HTTP RST
then another GET request comes in from Win7

This pattern is repeated 3 times before Win7 lets go and terminates the fetch.

Then the Windows prompt appears "cannot play this file"

```

---

### Post by nickrout on 2012-06-07
> **nhtrader said:**
> For you I did a fresh install on Win7 of FF 13.0.

1. I tried ASX feature and playback failed. The same message appeared.
2. then I installed the windows-firefox-plugin (b/c it is suppose to help with playback of windows media formats)
3. Again, the ASX feature failed to playback the video. The same message appeared. 


In an effort to delve into this more deeply. I downloaded and installed the wireshark pkg on mythbox. Set it up and got the following headers:

NOTE: I tried several methods. For comparison the HTTP headers for both the Direct Download and the ASX streaming mode are shown for the same TV show. Developers viewing these headers may notice that I modified mythweb's URL. I added the extension .asf and removed one of the slashes from the "double-slash". I did this to rule out any doubt that the URL was problematic for IE9. (it didn't make a difference. I still can't use ASX as "click & play")



I don't usually shout in emails or forums, but HOW MANY TIMES DO I HAVE TO SAY THAT THESE ARE NOT ASF FILES, THEY ARE MPG. I am guessing that brain dead windows software is trying to play the file as an asf file. But to say it again THE FILES ARE MPEG, specifically MPEG-TS.

So try making your code change the suffix to mpg.

---

### Post by nhtrader on 2012-06-07
> **nickrout said:**
> I don't usually shout in emails or forums, but HOW MANY TIMES DO I HAVE TO SAY THAT THESE ARE NOT ASF FILES, THEY ARE MPG. I am guessing that brain dead windows software is trying to play the file as an asf file. But to say it again THE FILES ARE MPEG, specifically MPEG-TS.

So try making your code change the suffix to mpg.

Your frustrated; imagine how I feel. I guess you didn't get the memo. Earlier in the thread I had reported that 3 extensions didn't work (failed to initiate automatic playback in IE) using: default mythweb extension(none), .mpg or .asf.


But for you, here are the HTTP headers for an HTTP request from Win7 using IE9 and clicking mythweb's ASX feature:

You see. It doesn't matter which of the three extensions are used. The response is the same.


```

GET //mythweb/pl/stream/3111/1338597000.asx HTTP/1.1
Accept: text/html, application/xhtml+xml, */*
Referer: http://192.168.0.8/mythweb/tv/recorded
Accept-Language: en-US
User-Agent: Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Win64; x64; Trident/5.0; MAAU)
UA-CPU: AMD64
Accept-Encoding: gzip, deflate
Host: 192.168.0.8
Connection: Keep-Alive
Cookie: mythweb_id=2tqq5l1secmt6rg18h2u6fcts0

HTTP/1.1 200 OK
Date: Thu, 07 Jun 2012 17:10:29 GMT
Server: Apache/2.2.22 (Ubuntu)
Content-disposition: attachment; filename="Antiques Roadshow - UK-.asx"
Content-length: 264
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/x-ms-asf; charset=ISO-8859-1

<ASX version = "3.0">
<TITLE>Antiques Roadshow - UK</TITLE>
<ENTRY>
<TITLE>Antiques Roadshow - UK - </TITLE>
<AUTHOR>MythTV - MythWeb</AUTHOR>
<COPYRIGHT>GPL</COPYRIGHT>
<REF HREF = "http://192.168.0.8:80//mythweb/pl/stream/3111/1338597000.mpg" />
</ENTRY>
</ASX>

--------------------------------------------------

GET /mythweb/pl/stream/3111/1338597000.mpg HTTP/1.1
Accept: */*
User-Agent: Windows-Media-Player/12.0.7601.17514
Accept-Encoding: gzip, deflate
Host: 192.168.0.8
Connection: Keep-Alive

HTTP/1.1 200 OK
Date: Thu, 07 Jun 2012 17:10:33 GMT
Server: Apache/2.2.22 (Ubuntu)
Accept-ranges: bytes
Content-disposition: attachment; filename="Antiques Roadshow - UK.mpg"
Content-length: 710088408
Last-Modified: Sat, 02 Jun 2012 01:01:00 GMT
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/mpeg; charset=ISO-8859-1

--------------------------------------------------
at this point handshaking stops and the following event occurs
TCP - HTTP RST
handshaking resumes with the following:
--------------------------------------------------

GET /mythweb/pl/stream/3111/1338597000.mpg HTTP/1.1
Cache-Control: no-cache
Connection: Keep-Alive
Pragma: getIfoFileURI.dlna.org
Accept: */*
If-Unmodified-Since: Sat, 02 Jun 2012 01:01:00 GMT
Range: bytes=3833856-710088407
User-Agent: NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514
GetContentFeatures.DLNA.ORG: 1
Host: 192.168.0.8

HTTP/1.1 206 Partial Content
Date: Thu, 07 Jun 2012 17:10:33 GMT
Server: Apache/2.2.22 (Ubuntu)
Accept-ranges: bytes
Content-disposition: attachment; filename="Antiques Roadshow - UK.mpg"
Content-length: 706254552
Content-range: bytes 3833856-710088407/710088408
Last-Modified: Sat, 02 Jun 2012 01:01:00 GMT
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/mpeg; charset=ISO-8859-1


```

This is exasperating for me as well. I've put this issue out there into MSFT's Technet and no responses yet. I've put this issue out to gecko-mediaplayer-plugin devs and no responses yet.

All I've been able to establish this far is:
1. my browser settings/mime types are ok
2. I have the necessary webbrowsers plugins and appropriate settings.
3. my video codecs are ok
4. my home network is ok
5. VLC works great. (but my goal is to get "ASX" feature to click & play)
Therefore, I am trying to learn how to activate/utilize this feature with a standard install of Win7 and IE.

6. this behavior is consistent among all of my WinPCs
7. This behavior appears across all of my webbrowsers: IE, FF, Opera, Chromium
8. On Ubuntu side; gecko-mediaplayer v1.0.4 plugin doesn't work either, but v0.9.9.2 does.
9. extensions are irrelavent to mythweb. Mythweb will serve up/transfer a video file with any extension, whether it exists or not, using wget: (examples)
 [http://mythweb/path/3111/1338597000.mpg](http://mythweb/path/3111/1338597000.mpg) (exists and downloads)
 [http://mythweb/path/3111/1338597000.asf](http://mythweb/path/3111/1338597000.asf) (doesn't exist but downloads anyway)
 [http://mythweb/path/3111/1338597000](http://mythweb/path/3111/1338597000) (doesn't exist but downloads anyway)
 [http://mythweb/path/3111/1338597000.joe](http://mythweb/path/3111/1338597000.joe) (doesn't exist but downloads anyway)

---

### Post by azmyth on 2012-06-07
I suspect WMP looks at the file extension and then sets the mime type based on the extension. I could be incorrect but from looking at your headers the mime type is set to mpeg and I believe mpeg ts is a different mime type. WMP probably tries to play the partial mpeg file not knowing it's a stream and when WMP realizes it's missing most of the file it kicks an error saying no codec. I would try but WMP can't handle digest authtype.

You could just use VLC and set the Windows to use vlc for the .asx extension and you'll have click and play.

Personally, I think you're trying to solve something that may not be solvable with WMP.

---

### Post by nickrout on 2012-06-07
> **nhtrader said:**
> Your frustrated; imagine how I feel. I guess you didn't get the memo. Earlier in the thread I had reported that 3 extensions didn't work (failed to initiate automatic playback in IE) using: default mythweb extension(none), .mpg or .asf.


But for you, here are the HTTP headers for an HTTP request from Win7 using IE9 and clicking mythweb's ASX feature:

You see. It doesn't matter which of the three extensions are used. The response is the same.


```

GET //mythweb/pl/stream/3111/1338597000.asx HTTP/1.1
Accept: text/html, application/xhtml+xml, */*
Referer: http://192.168.0.8/mythweb/tv/recorded
Accept-Language: en-US
User-Agent: Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Win64; x64; Trident/5.0; MAAU)
UA-CPU: AMD64
Accept-Encoding: gzip, deflate
Host: 192.168.0.8
Connection: Keep-Alive
Cookie: mythweb_id=2tqq5l1secmt6rg18h2u6fcts0

HTTP/1.1 200 OK
Date: Thu, 07 Jun 2012 17:10:29 GMT
Server: Apache/2.2.22 (Ubuntu)
Content-disposition: attachment; filename="Antiques Roadshow - UK-.asx"
Content-length: 264
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/x-ms-asf; charset=ISO-8859-1

<ASX version = "3.0">
<TITLE>Antiques Roadshow - UK</TITLE>
<ENTRY>
<TITLE>Antiques Roadshow - UK - </TITLE>
<AUTHOR>MythTV - MythWeb</AUTHOR>
<COPYRIGHT>GPL</COPYRIGHT>
<REF HREF = "http://192.168.0.8:80//mythweb/pl/stream/3111/1338597000.mpg" />
</ENTRY>
</ASX>

--------------------------------------------------

GET /mythweb/pl/stream/3111/1338597000.mpg HTTP/1.1
Accept: */*
User-Agent: Windows-Media-Player/12.0.7601.17514
Accept-Encoding: gzip, deflate
Host: 192.168.0.8
Connection: Keep-Alive

HTTP/1.1 200 OK
Date: Thu, 07 Jun 2012 17:10:33 GMT
Server: Apache/2.2.22 (Ubuntu)
Accept-ranges: bytes
Content-disposition: attachment; filename="Antiques Roadshow - UK.mpg"
Content-length: 710088408
Last-Modified: Sat, 02 Jun 2012 01:01:00 GMT
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/mpeg; charset=ISO-8859-1

--------------------------------------------------
at this point handshaking stops and the following event occurs
TCP - HTTP RST
handshaking resumes with the following:
--------------------------------------------------

GET /mythweb/pl/stream/3111/1338597000.mpg HTTP/1.1
Cache-Control: no-cache
Connection: Keep-Alive
Pragma: getIfoFileURI.dlna.org
Accept: */*
If-Unmodified-Since: Sat, 02 Jun 2012 01:01:00 GMT
Range: bytes=3833856-710088407
User-Agent: NSPlayer/12.00.7601.17514 WMFSDK/12.00.7601.17514
GetContentFeatures.DLNA.ORG: 1
Host: 192.168.0.8

HTTP/1.1 206 Partial Content
Date: Thu, 07 Jun 2012 17:10:33 GMT
Server: Apache/2.2.22 (Ubuntu)
Accept-ranges: bytes
Content-disposition: attachment; filename="Antiques Roadshow - UK.mpg"
Content-length: 706254552
Content-range: bytes 3833856-710088407/710088408
Last-Modified: Sat, 02 Jun 2012 01:01:00 GMT
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: video/mpeg; charset=ISO-8859-1


```

This is exasperating for me as well. I've put this issue out there into MSFT's Technet and no responses yet. I've put this issue out to gecko-mediaplayer-plugin devs and no responses yet.

All I've been able to establish this far is:
1. my browser settings/mime types are ok
2. I have the necessary webbrowsers plugins and appropriate settings.
3. my video codecs are ok
4. my home network is ok
5. VLC works great. (but my goal is to get "ASX" feature to click & play)
Therefore, I am trying to learn how to activate/utilize this feature with a standard install of Win7 and IE.

6. this behavior is consistent among all of my WinPCs
7. This behavior appears across all of my webbrowsers: IE, FF, Opera, Chromium
8. On Ubuntu side; gecko-mediaplayer v1.0.4 plugin doesn't work either, but v0.9.9.2 does.
9. extensions are irrelavent to mythweb. Mythweb will serve up/transfer a video file with any extension, whether it exists or not, using wget: (examples)
 [http://mythweb/path/3111/1338597000.mpg](http://mythweb/path/3111/1338597000.mpg) (exists and downloads)
 [http://mythweb/path/3111/1338597000.asf](http://mythweb/path/3111/1338597000.asf) (doesn't exist but downloads anyway)
 [http://mythweb/path/3111/1338597000](http://mythweb/path/3111/1338597000) (doesn't exist but downloads anyway)
 [http://mythweb/path/3111/1338597000.joe](http://mythweb/path/3111/1338597000.joe) (doesn't exist but downloads anyway)

I am awaiting your post to the mailing list.

---

### Post by nhtrader on 2012-06-07
> **azmyth said:**
> 
Personally, I think you're trying to solve something that may not be solvable with WMP.

I'm glad someone new is bringing this point to light, and not me. Are you saying it is a bug? I'm not. I'm assuming that my system isn't configured properly; or it is missing a component/dll/plugin; or a setting is missing; or some other bit windows is set to work with mythweb. And I was hoping that the solution would be forth coming due to an obvious oversight on my part. As of today, this isn't the case.

My position on this is simple. MythTV was engineered with this "ASX" feature and all I'm trying to do is use it. I was hoping this would be rather simple since this feature has been around for a long time. But it turns out, a feature that was implemented for the sole purpose to appease Window Users (because ASX is a MSFT streaming protocol) isn't so easy to use. And more importantly, it's not so easy/obvious to activate. I have not been able to get any of my Win7 PCs to "click & play". Do yours?

I'm merely trying to use "ASX" and show others that may have the same problem what details are involved in understanding why WMP won't perform as expected. Thus far, the nooks and crannies that I've poke into haven't brought to light the offending "thing", and hasn't sparked any new insights. Hopefully someone knowledgable with regards to this streaming protocol can identify what the problem is.

I'm hoping that the HTTP headers will spark some new insights as it is now clearer as to what is going on. But giving up and just forgetting about it; would be easier.

---

### Post by azmyth on 2012-06-07
Mine works but only with VLC. I like VLC better so I just install it when I get a new computer. I just clicked on the ASX icon in mythweb and it said what to use and I said VLC and then checked use all the time. Done. Now when I click on the icon it just pulls up VLC and then asks me for my password since I have auth set to digest in Apache.

I'm not sure if it's a bug in WMP as it more of how it handles files. I believe it just looks at the extension and says it needs so and so codec whether it's right or wrong whereas VLC looks at the header info to get the correct codec. I just believe WMP is made for the masses whereas VLC takes input from users.

---

### Post by nickrout on 2012-06-07
> **nhtrader said:**
>  But it turns out, a feature that was implemented for the sole purpose to appease Window Users (because ASX is a MSFT streaming protocol) isn't so easy to use. And more importantly, it's not so easy/obvious to activate.Just because MS wrote the sepc doesn't mean it is just implemented for MS users>  I have not been able to get any of my Win7 PCs to "click & play". Do yours?you constantly contradict yoursefl. First you say click and play works on VLC now you say it doesn't.> 

I'm merely trying to use "ASX" and show others that may have the same problem what details are involved in understanding why WMP won't perform as expected. Thus far, the nooks and crannies that I've poke into haven't brought to light the offending "thing", and hasn't sparked any new insights. Hopefully someone knowledgable with regards to this streaming protocol can identify what the problem is.

I'm hoping that the HTTP headers will spark some new insights as it is now clearer as to what is going on. But giving up and just forgetting about it; would be easier.

---

### Post by tgm4883 on 2012-06-07
> **nickrout said:**
> Just because MS wrote the sepc doesn't mean it is just implemented for MS users

To add onto that. Just because MS wrote the spec, doesn't mean they implement it completely. (or correctly)

---

### Post by nickrout on 2012-06-07
> **tgm4883 said:**
> To add onto that. Just because MS wrote the spec, doesn't mean they implement it completely. (or correctly)

or document it properly!

---

### Post by nhtrader on 2012-06-08
> **nickrout said:**
> you constantly contradict yoursefl. First you say click and play works on VLC now you say it doesn't.

There is no contradiction.

In all instances, I DO NOT HAVE THE ABILITY TO "CLICK & PLAY" on a Windows PC using IE. So do you have any insights as to how to do this?

Can I "click & play" with VLC? Yes, with a third party browser. However, the point of this thread is to show me how to use a Windows based streaming protocol using Windows products. 

Apparently, you don't know the answer. I'm hopeful someone will know the answer.

BTW, let's not forget that on the ubuntu side, even the new version of the gecko-mediplayer-plugin can't stream using Mythweb's "ASX".

---

### Post by nickrout on 2012-06-09
I don't know what gecko-mediaplayer-plugin is. I click on the asx link in ubuntu and the file opens and streams in totem.

---

### Post by azmyth on 2012-06-09
What happens when you click on the AXS icon in mythweb while you're in IE. Does it prompt you to open the asx file? IE doesn't seem to allow me to open automatically. You may have your settings in IE set too high and it's not allowing it as it should prompt you to open or save.

---

### Post by nhtrader on 2012-06-11
> **azmyth said:**
> What happens when you click on the AXS icon in mythweb while you're in IE. Does it prompt you to open the asx file? IE doesn't seem to allow me to open automatically. You may have your settings in IE set too high and it's not allowing it as it should prompt you to open or save.

When I click on the "ASX" icon, IE9 responds with a prompt at the bottom of the window "Do you want to open or save? Open Save Cancel. 

I have tried both the Open and Save buttons. The "Save" button stores a small (260 bytes) XML file. The "Open" Button causes WMP to appear and then the prompt appears: Windows Media Player cannot play the file. The player might not support the file type or might not support the codec that was used to compress the file. Two buttons appear "Close" and "Web Help". The video does not play.

Again, I have not installed any additional codecs and I'm not interested in doing so. I'm looking to learn how a standard installation of Win7 with IE can play mythweb's "ASX" streamed video.

Does this "ASX" feature of mythweb work for you on your Win7/IE PC?

---

### Post by nickrout on 2012-06-11
> **nhtrader said:**
> When I click on the "ASX" icon, IE9 responds with a prompt at the bottom of the window "Do you want to open or save? Open Save Cancel. 

I have tried both the Open and Save buttons. The "Save" button stores a small (260 bytes) XML file. The "Open" Button causes WMP to appear and then the prompt appears: Windows Media Player cannot play the file. The player might not support the file type or might not support the codec that was used to compress the file. Two buttons appear "Close" and "Web Help". The video does not play.

Again, I have not installed any additional codecs and I'm not interested in doing so. I'm looking to learn how a standard installation of Win7 with IE can play mythweb's "ASX" streamed video.

Does this "ASX" feature of mythweb work for you on your Win7/IE PC?

And just to be clear, does this happen even when you make the change to mythweb code to add a mpg extension to the filename?

---

### Post by nhtrader on 2012-06-11
> **nickrout said:**
> And just to be clear, does this happen even when you make the change to mythweb code to add a mpg extension to the filename?

yes

---

### Post by azmyth on 2012-06-11
You need to set asx to open with VLC. You need to navigate to this location below in control panel under win7

Control Panel -> Programs -> Default Programs -> Set Associations

Scroll to the asx extension and right mouse click then change association to VLC.

---

### Post by nhtrader on 2012-06-12
> **azmyth said:**
> You need to set asx to open with VLC. You need to navigate to this location below in control panel under win7

Control Panel -> Programs -> Default Programs -> Set Associations

Scroll to the asx extension and right mouse click then change association to VLC.

Thank you, but this work around has been stated previously. 

Again, I'm only interested in figuring out how to get MythTV recordings to playback on Win7 and IE with its native codecs and plugins without any other third party software.

---

### Post by nickrout on 2012-06-12
I will suggest the mailing list again. It is the definitive place for help on mythtv, not here. You will get developers hanging there, very few here. Probably even the author of the code concerned.

If you find a solution post back here of course. In the meantime, please do as I suggest :)

---

