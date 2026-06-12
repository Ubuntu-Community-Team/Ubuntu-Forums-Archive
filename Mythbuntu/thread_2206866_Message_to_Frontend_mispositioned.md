---
title: "Message to Frontend mispositioned"
date: 2014-02-21
forum: Mythbuntu
---

### Post by ceesquared on 2014-02-21
A call = echo "message Frontend to Standby in 2 mins" | telnet 127.0.0.1 6546 > /dev/null results in a message box which is centred on the bottom right of the screen. The OK button cannot be seen but there is a response when OK is pressed on the remote, so the message box works but it is just out of position. I am using theme Readability but I have also had it with Mythbuntu Wide. Where do I find the xml script for the message box and what do I have to reset to get the message centred?

---

### Post by blm-ubunet on 2014-02-21
I don't think mythtv supports a true telnet interface..you are meant to use mythutil --meassage...

for example a notitication message:
```
`/usr/local/bin/mythutil --bcastaddr 192.168.1.1  --notification
--type normal --origin "Start Script" --message_text "$message"
--description "Myth Frontend" --timeout=2 --syslog local7`
```
or can use netcat
```
netcat -uv -q1 -w 0 mythbe01 6948 < message.txt
```

where message.txt is
```
<mythmessage version="1">
  <text> Test Message Text</text>
  <timeout>5</timeout>
</mythmessage>
```

  didn't try to get this to work tho..
```
<mythnotification version="1">
   <container name="news_scroller">
      <textarea name="text_scroll">
         <value>Testing</value>
      </textarea>
   </container>
</mythnotification>
```

think the scrolling "news" ticker does not exist anymore..

---

### Post by ceesquared on 2014-02-24
Thanks blm-ubunet but i am afraid you are wrong. Telnet is supported. I have now tried two routes to get a message displayed.:=
echo "message Frontend to Standby in 2 mins" | telnet 127.0.0.1 6546 > /dev/null  -- works in a fashion as does :=
GET  127.0.0.1:6547/Frontend/SendMessage?Message="To Standby in 2 min" (API call)
The results are interesting. If I am watching live TV or a recording ( both the same as far as MythTV is concerned I suppose)  then the message is centred off the bottom right of the screen. If I am in a menu, any menu, then the message is correctly centred on the screen. So the question is, is this a theme fault or is it a MythTV bug? How do I solve it?

---

### Post by blm-ubunet on 2014-02-24
No I'm not..you are.

[http://www.mythtv.org/wiki/Telnet](http://www.mythtv.org/wiki/Telnet)

[http://www.gossamer-threads.com/lists/mythtv/users/544132#544132](http://www.gossamer-threads.com/lists/mythtv/users/544132#544132)

---

### Post by ceesquared on 2014-02-25
Thanks blm-ubunet, lets call it a draw. Yes, telnet is depreciated, but it does work for what I am using it for. It does not answer the main question however. Why in a menu is the message box correctly displayed but in live TV/watching recording it is totally out of scale and position? Perhaps this is a case for a bug report.

---

### Post by blm-ubunet on 2014-02-25
If you use or mention telnet you will not get any traction with bug report..
AFAIK Telnet was never supported.
You need to confirm the same with mythutil.

I use mythtv master & "mythbuntu wide" theme; notifications (mythutil) & messages (netcat) are correctly positioned in menus & playback.
I do use the same fixed video mode for GUI & playback.

Do you have a video mode change between playback & GUI ?

---

### Post by ceesquared on 2014-02-27
1. I do not have a video change between GUI & playback.
2. I have confirmed problem with both API call and mythutil, I have not tried netcat.
I am using a combined FE/BE, are you? If not could this be the problem? My box is not internet connected so changing themes is a problem, which could be the next thing to check. If you are successful with your theme then it must be a theme bug so we are back to the original question, what do I edit? If a different message box is used between menu and playback then I may need to look there. Just in case you cannot come up with any other ideas , I will investigate asking the theme designer.

---

### Post by blm-ubunet on 2014-02-27
I have dev & main prodn system (both combined FE & BE).

I can send netcat messages from 4 different PCs to either FEs (local box & LAN)
I can send mythutil messages from 2 diff PCs to either FEs (local & LAN)

There have been many theme changes to support the new message notifications..
Note I'm running git master & latest mythbuntu wide theme.

You can download the latest theme from git just like source code.
You can just replace the existing or save as new name.
You pick the new theme or new theme name from FE setup screen.

---

### Post by ceesquared on 2014-03-06
Just an update. I have copied over the latest Readability theme from GitHub with the same result - misplaced message box on watch tv. Would deleting all  the surplus themes on the disk help?

---

### Post by blm-ubunet on 2014-03-06
Why would it?

I just tried "Readability" theme (actually very nice) on master & messages are correctly positioned.
(Message sent with netcat just as posted previous)

Notifications are also correctly positioned (sent via mythutil...).

You not still sticking/stuck to telnet are you ?

---

### Post by ceesquared on 2014-03-07
I have converted my call to GET, so that is not the problem
shuttime=`date '+%I:%M' -d '+15 minutes'`
GET  127.0.0.1:6547/Frontend/SendMessage?Message="To Standby at $shuttime"
This is getting very odd. I have a USB radio link on order and when it arrives I will try and see if there is an update to Mythtv which will cure the problem.

---

### Post by blm-ubunet on 2014-03-07
Your GET command works fine on master with mythbuntu wide & readability theme.

Re you using --geometry overrides or using the screen wizard over/underscan correction/adjustment ?

Your GET command works with --geometry override here (for a screen smaller than my main FE screen).

---

### Post by ceesquared on 2014-03-10
I will check when I have a chance. You might like to see [https://github.com/MythTV-Themes/Readability/issues/1#issuecomment-37117111](https://github.com/MythTV-Themes/Readability/issues/1#issuecomment-37117111)

---

### Post by blm-ubunet on 2014-03-10
The message is correctly positioned with Readability theme on master.
That using using openGL painter & VDPAU video playback.

Could the problem relate to Qt, openGL or openGL2 painters ?
Or the video playback method?

As an aside..
Don't find readability works very well with large lists of recordings because the page up & down are mapped to just up & down functions. Will have to work out a patch.

---

### Post by ceesquared on 2014-03-26
I am using on-board chip(intel) for graphics output, not a graphics card. Could this be the difference? I have found that pg up and pg down do work on large lists but you have to use 1 cursor down call to get it from the title bar ( All recordings) to the first recording on the list and then pgup and pgdown will work.

---

### Post by ceesquared on 2014-07-23
To any more readers, especially blm-ubunet. I have further information. Firstly my setup. I have HDMI HD output to an HD TV. I receive through freesat (UK tv) both SD and HD. If the FE is displaying a SD broadcast then the message box is out of place as described. If however, an HD broadcast is being shown then the message box is correct! This may explain why blm-ubunet does not have a problem. Perhaps it is a case of SD  broadcast/SD output or HD broadcast/ HD output is ok but mixing them screws the output. In this case is it a theme problem or could it be a mythtv problem? If the Message box is "pasted" onto the display before conversion SD to HD and using the broadcast parameters then it should be OK, if after, and the box pixel position is calculated from the output parameters, the the box will be to far right and down.

---

