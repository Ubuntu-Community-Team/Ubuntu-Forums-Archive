---
title: "[SOLVED] No DVD playback on Toshiba with Intel 945GM"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by KnowYourEnemy626 on 2007-08-28
I have been trying for about 2 days to unsuccessfully get my Toshiba Satellite A105-S4114 to play DVDs. I am running Feisty and I believe I have downloaded all the appropriate codecs for DVD playback including libdvdcss2 which seems to be the one most commonly needed. My graphics card is an Intel 945GM.  I have Totem-xine, Mplayer, vlc, smplayer, and gxine installed, none of which will play DVDs. When I tell Totem to play a DVD it just disappears. MPlayer gives me a window that says "Fatal error!  Error opening/initializing the selected video_out (-vo) device." VLC and gxine also disappear when i tell them to play the DVD. To me this seems like more of an issue with my video hardware than with codecs. Hopefully someone that knows more can help me out. Thank you.

---

### Post by Metacarpal on 2007-08-28
Open a terminal (Applications menu -> Accessories -> Terminal) and type (or copy-paste):

```
aptitude show libdvdcss2 | grep installed
```

Your output should be:

```
State: installed
Automatically installed: yes
```

If that's not what you get, you'll need to install the package libdvdcss2, which is not available in the regular Ubuntu repos.  You'll need to [add the Medibuntu repos]("https://help.ubuntu.com/community/Medibuntu").  Take note that installing that package may represent legal issues due to copyright laws, depending on where you live.

If you have libdvdcss2 installed already... Well, I don't know how to help you.  Have you checked that you're using the correct DVD region code?

---

### Post by KnowYourEnemy626 on 2007-08-28
when i put in your code, my this is my output


State: installed
Automatically installed: no


so i assume that means its there, it just wasnt installed automatically?

---

### Post by KnowYourEnemy626 on 2007-08-28
This problem was solved by another user. Thanks for your help.

---

### Post by Rhubarb on 2007-08-30
Could you please share with me how you managed to fix the problem?

---

### Post by KnowYourEnemy626 on 2007-08-30
somebody sent me these instructions

"I swear this comes up more often then anything here. But there is a way to do it but is starts with a question

Do you have Medibntu installed? You could use the install trick posted in the sticky but I say heading to the Medibuntu site and using their Terminal install command lines are frankly easier.

Next head on over to Add Remove on your own system and look for GS Streamer and install all of them.

Return to terminal and use this command " sudo apt-get update "

Then head here [http://www.getautomatix.com/wiki/ind...e=Installation](http://www.getautomatix.com/wiki/ind...e=Installation)

PLEASE keep in mind when using the program Automatrix installs it is a borderline illegal program and when your using it to install the codecs you need act like your not living in the US or they won't install

Lastly head over to add remove again and get the Kaffiene player it frankly plays DVDs better than anything else

You should be playing DVDs all regions after this."

---

