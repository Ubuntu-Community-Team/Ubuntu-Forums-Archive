---
title: "Streaming an online radio station"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by thetido on 2007-02-27
I want to listen to [WSB AM 750](http://wsbradio.com/) here in Atlanta, but they do their streaming through a 3rd party company called [Stream Audio](http://www.streamaudio.com).  Stream Audio has a horrible little popup that loads WMP (or in this case mplayer plugin).  In (k)ubuntu, the popup messes up pretty badly, and it takes forever for the stream to work.  It WILL work, but you have to keep the popup in the foreground window - which is really annoying.  I'd like to just play the stream directly through a player, but that's proving to be very difficult.  

I tried putting the stream URL in, but that was no go.  Then I tried to make a local html file with the code from the popup, but that didn't work either:

```
<OBJECT ID="NSPlay" classid="CLSID:6BF52A52-394A-11d3-B153-00C04F79FAA6" standby="Loading Microsoft Windows Media Player components..." type="application/x-oleobject" width="275" height="22"><PARAM NAME="URL" VALUE="http://www.streamaudio.com/stations/player/pages/newplayer/auth/GenerateASX1.asp?t1=cc244e467521aa385031bd99f51f5198&s=680&y=2007&m=2&d=27&hh=9&mm=45&ss=50">
<PARAM NAME="AnimationatStart" VALUE="true">
<PARAM NAME="TransparentatStart" VALUE="true">
<PARAM NAME="AutoStart" VALUE="true">
<PARAM NAME="ShowControls" VALUE="0">
<PARAM NAME="ShowStatusBar" VALUE="1">
<PARAM NAME="enableContextMenu" VALUE="False">

<PARAM NAME="BufferingTime" VALUE="5">
<EMBED TYPE="application/x-mplayer2"
SRC="http://www.streamaudio.com/stations/player/pages/newplayer/auth/GenerateASX1.asp?t1=cc244e467521aa385031bd99f51f5198&s=680&y=2007&m=2&d=27&hh=9&mm=45&ss=50"
NAME="NSPlay"
ShowStatusBar="true"
ShowCaptioning="false"
ShowControls="false"
ShowPositionControls="false"
showtracker="false"
SubpictureOn="false"
EnableContextMenu="0"
Width="275"
Height="22"
BufferingTime="5"
>
</EMBED>
</OBJECT>
```

Anyone clever have an idea how to get around popup hell?

---

### Post by Shay Stephens on 2007-02-27
When the popup is playing, you can minimize the popup and then you should be able to go to other windows or workspaces and the audio will keep playing.  At least that works for me in gnome.

---

### Post by panch0 on 2007-02-27
If the popup works in Konqueror, the easiest thing is to make KPlayer the default player, and then when the popup appears, right click on the video area and choose Start KPlayer. That will open the standalone KPlayer and play the stream in it.

---

