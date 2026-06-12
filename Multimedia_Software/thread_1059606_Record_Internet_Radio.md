---
title: "Record Internet Radio"
date: 2009-02-03
forum: Multimedia Software
---

### Post by slick666 on 2009-02-03
Here is one area that I'm trying to switch from OSX to Ubuntu. Right now is OSX I can start listening to the streamed version of a radio station. I can then save that in an MOV file that (of course) I cannot play with any other player other than quicktime. What I would like to do is setup on my ubuntu system a way to record my radio station much like a VCR so I can record the local news and shows I'm interested in and be able to play them when I get home. I can't seem to find this anywhere under linux but I'm sure it can be done. 

If I can listen to the radio on Ubuntu I should be able to pipe that output to an ogg or mp3 encoder instead of the speakers. I should then be able to set this as some sort of cron job so it will execute when I need to.

Any help would be appreciated this is one of the few remaining things I do in OSX that I can't seem to do in Ubuntu.

---

### Post by markbuntu on 2009-02-04
Streamripper will do that for you, or kstreamripper which is a KDE app. I played around with them a while ago and I seem to remember that incomplete streams ripped with kstreamripper will play but ones with steamripper would not. Something like that anyway.

You can use sound converter or soundKonverter to convert the saved stream. I think soundKonverter has more options than soundconverter.

They are all in the repos.

---

### Post by andrew.46 on 2009-02-04
Hi,

It can be done :-). I record an amazing radio broadcast called 'For the God Who Sings' every Sunday night and I have scripted this + run from cron. Have a look at:

Slackware and "For The God Who Sings"
[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

and just ignore all the slackware stuff.

Andrew

---

### Post by slick666 on 2009-02-04
There are some radio stations that I can navigate to with firefox and it opens with the "totem movie player". Is there a way that I can get the address I need from the player or from the the html code? What sort or address characteristics should I be looking for?

---

### Post by wolfen69 on 2009-02-04
> **slick666 said:**
> There are some radio stations that I can navigate to with firefox and it opens with the "totem movie player". Is there a way that I can get the address I need from the player or from the the html code? What sort or address characteristics should I be looking for?

just right click the link that launches radio player, and select "copy link location".

---

### Post by slick666 on 2009-02-05
The link launches a separate window. The link on the website is [http://www.910knew.com/cc-common/streaming_new/index.html?refreshed=yes]("http://www.910knew.com/cc-common/streaming_new/index.html?refreshed=yes") Thanks for your help.

---

### Post by slick666 on 2009-02-19
Ok I think I'm getting pretty close. I've looked through the html code of the page.

```

    <div id="player">
      <OBJECT ID = "MediaPlayer1" CLASSID = "CLSID:6BF52A52-394A-11d3-B153-00C04F79FAA6" width="300" height="64" >
        <PARAM Name="autoStart"  Value="true">
        <PARAM Name="uiMode" Value="mini">
        <PARAM NAME="URL" VALUE="http://www.910knew.com/cc-common/streaming_new/genasx.php?ua=fcbc23bca25f386c8798c6343ce620f6">
        <PARAM NAME="autoStart" VALUE="1">
        <PARAM NAME="ShowControls" value="1">

        <PARAM NAME="ShowStatusBar" value="1">
        <EMBED type="application/x-mplayer2"
          pluginspage="http://www.microsoft.com/Windows/MediaPlayer/"
          name="MediaPlayer1"
          uiMode="mini"
          src="http://www.910knew.com/cc-common/streaming_new/genasx.php?ua=fcbc23bca25f386c8798c6343ce620f6"
          url="http://www.910knew.com/cc-common/streaming_new/genasx.php?ua=fcbc23bca25f386c8798c6343ce620f6"
          width="300" height="64"
          animationatStart="false"
          transparentatStart="true"
          autostart="1"
          showControls="1"
          showStatusBar="1">
        </EMBED>
      </OBJECT>
    </div>

```

But I can't get it to play. I think this is the url but I can't open it with mplayer.

```
http://www.910knew.com/cc-common/streaming_new/genasx.php?ua=fcbc23bca25f386c8798c6343ce620f6
```

---

