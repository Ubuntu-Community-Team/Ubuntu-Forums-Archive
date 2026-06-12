---
title: "Bbc radio 4 web feed address anyone ?"
date: 2011-02-23
forum: Multimedia Software
---

### Post by BADGER.BRAD on 2011-02-23
Hello All,

I've tried to contact the BBC on this but they cleverly seem to have made this impossible ! Does anyone know if  there is a none Microsoft feed for radio 4, I have all my radio stations set up and working using Rhythmbox but cannot listen to radio 4 as it's a mms feed.

Any help Greatly appreciated

Brad

---

### Post by kvarley on 2011-02-23
You can listen to Radio 4 Live through their flash widget.

[http://www.bbc.co.uk/iplayer/radio/bbc_radio_fourfm/listenlive]("http://www.bbc.co.uk/iplayer/radio/bbc_radio_fourfm/listenlive")

---

### Post by nothingspecial on 2011-02-23
Here you go

BBC Radio 1 - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio1/radio1_bb_live_eq1_sl0
BBC Radio 2 - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio2/radio2_bb_live_eq1_sl0
BBC Radio 3 - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio3/radio3_bb_live_eq1_sl0
BBC Radio 4 - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4_bb_live_eq1_sl0
BBC Radio 5 Live - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio5/radio5_bb_live_eq1_sl0
BBC Radio 5 Live Extra - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio5/5spxtra_bb_live_eq1_sl0
BBC 6 Music - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/6music/6music_bb_live_eq1_sl0
BBC Radio 7 - mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/bbc7/bbc7_bb_live_eq1_sl0

---

### Post by BADGER.BRAD on 2011-02-23
I'm looking for a none mms feed so I can play directly in my radio player rather than having to use flash.Any takers?

Brad

---

### Post by nothingspecial on 2011-02-23
If you live in the UK, those urls will work in Rhythmbox, mplayer, radiotray etc -

if you don't ???????

I just tried them all.

---

### Post by nothingspecial on 2011-02-23
Also you can type (copy and paste) this into a terminal. mplayer treats the asx urls as playlists and will stream them using the -playlist flag.
```

mplayer -playlist http://bbc.co.uk/radio/listen/live/r4.asx 
```

Obviously you don't want to have to type that lot everytime you want to listen to Desert Island Disks, so do this
```

echo 'alias r4="mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r4.asx < /dev/null &"' | tee -a ~/.bashrc
```

Then type ```
. ~/.bashrc
```

Now every time you want to listen to radio 4, open a terminal and type
```

r4
```

Again, if you don't live in the UK I don't think this works.

---

### Post by BADGER.BRAD on 2011-02-23
Thanks for all your input everyone, it really is much appreciated.When I try to listen to any mms feed in Rhythmbox I get  NO URI HANDLER IMPLEMENTED FOR "MMS" ( THE SAME WITH OTHER PLAYERS)
Does this mean I am maybe missing some software somewhere ?

Again many thanks all

Brad UK

---

### Post by nothingspecial on 2011-02-23
Do you have the non-free-codecs package installed?

I don't know why those urls don't work for you. Just tried them on 3 different Ubuntu boxes.

---

### Post by BADGER.BRAD on 2011-02-23
I have been doing a little research, and now think it is down to not having the codecs for mms file as suggested by Nothingspecial.I tried to load them but but I get a screen asking me to agree with Microsofts licence and as I don't what anything to do with Microsoft I have now decided that Radio 4 will have to be consigned to the scap bin.

Thanks for the help everyone.

Brad

---

