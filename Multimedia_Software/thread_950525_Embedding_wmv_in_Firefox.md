---
title: "Embedding wmv in Firefox??"
date: 2008-10-17
forum: Multimedia Software
---

### Post by fidgaf on 2008-10-17
Sorry if this is the wrong place (please move if it is) but Firefox is driving me nuts trying to embed a wmv file in a webpage.

```
<embed type="application/x-mplayer2" src="http://webpage.url/videofile.wmv" name="MediaPlayer" width="450" height="300" showcontrols="1" autostart="0" >
```

Suggestions on the web don't seem to settle on parameter values. They can be "True", "true", 1 or "1". Maybe it doesn't matter.

My Firefox refuses to recognise any showcontrols. It does for about half a second then the controls disappear.

In some Firefox it insists on only showing the top left-hand quarter of the video.

I have absolutely no problems with Chrome, Opera, IE etc.

Any suggestions?

Thanks.

.

---

### Post by uwwillay on 2008-11-22
I have the same problem :(

I did find a workaround though:

*Right click on the page and click "view source"
*Find the link to the imbedded video
*copy that link
*now open "movie player" under applications>sound and video
*click movie and open location
*paste the link and click open

It will stream the video directly to movie player and you can enjoy full controls

Kind of a pain, but at least it works...

---

### Post by fidgaf on 2008-11-22
Thank you for that tip. Very useful.

I must say, much as I want FF to be the No. 1 browser, letting details like this fall through the development cycle in the multi-media world of today is bordering on the criminal.

Not everyone is going to bother with little fixes and work-arounds. Most people are going to say "Doesn't work" and reach for uninstall.

Multi-media should be the top, top, top priority and it should work "out-of-the-box" - Period!

.

---

### Post by WDBMagic on 2009-01-01
Hi,

While looking for a similar answer to your problem, I cam across someone who had the same problem but in reverse. ie it worked in Firefox but not IE7

Anyway I tried it and it worked for me in both Firefox and IE7. Hope it does for you.

Code:
<!-- begin embedded WindowsMedia file... --> <table border='0' cellpadding='0' align="center"> <tr><td> <OBJECT id='mediaPlayer' width="704" height="573" classid='CLSID:22d6f312-b0f6-11d0-94ab-0080c74c7e95' codebase='http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab#Version=5,1,52,701' standby='Loading Microsoft Windows Media Player components...' type='application/x-oleobject'> <param name='fileName' value="../content/Video/video.wmv"> <param name='animationatStart' value='true'> <param name='transparentatStart' value='true'> <param name='autoStart' value="true"> <param name='showControls' value="true"> <param name='loop' value="true"> <EMBED type='application/x-mplayer2' pluginspage='http://microsoft.com/windows/mediaplayer/en/download/' id='mediaPlayer' name='mediaPlayer' displaysize='4' autosize='-1' bgcolor='darkblue' showcontrols="true" showtracker='-1' showdisplay='0' showstatusbar='-1' videoborder3d='-1' width="704" height="573" src="../content/Video/video.wmv" autostart="true" designtimesp='5311' loop="true"> </EMBED> </OBJECT> </td></tr> <!-- ...end embedded WindowsMedia file --> <!-- begin link to launch external media player... --> <tr><td align='center'> </td></tr> </table>

---

### Post by fidgaf on 2009-01-02
Thanks for that info. I will give it a try as soon as I can.

---

### Post by wolfen69 on 2009-01-02
what is the link you are having trouble with?

---

