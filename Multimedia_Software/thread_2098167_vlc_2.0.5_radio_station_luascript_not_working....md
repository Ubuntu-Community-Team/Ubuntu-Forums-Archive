---
title: "vlc 2.0.5 radio station luascript not working..."
date: 2012-12-25
forum: Multimedia Software
---

### Post by andrew.46 on 2012-12-25
There is a nice lua script that allows radio streaming with a great interface with vlc:

Extending VLC with Lua
[http://www.coderholic.com/extending-vlc-with-lua/](http://www.coderholic.com/extending-vlc-with-lua/)

I have used this for some time but upon installing vlc 2.0.5 I am unable to get it to work: the menu with the various radion stations shows up well enough but nothing will play. The streams themselves play well enough directly with vlc.

---

### Post by bretonfou on 2012-12-25
I just instaled it, and i m listening to baroque venice music (beauty).


i just did :

 mkdir -p ~/.local/share/vlc/lua/extensions

and i copied that file into it : 


> 
--[[
 Streaming Radio Player extension for VLC &gt;= 1.1.0
 Authors: Ben Dowling ([http://www.coderholic.com](http://www.coderholic.com))
--]]
 
stations = {

{ name = "Classic FM", url = "http://mediaweb.musicradio.com/Show.asx?StreamID=2" },
{ name = "BBC Radio3 HD", url = "http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls" },
{ name = "Norway Radio Klassisk 192", url = "http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h" },
{ name = "Radio Mozart", url = "http://listen.radionomy.com/radio-mozart.m3u" },
{ name = "Poland", url = "http://91.121.92.167:8900" },
{ name = "Classical Persian http://www.iranianradio.com/#", url = "http://213.73.255.244:10700" },
{ name = "Radio-Orfei RUSSIA", url = "mms://live.rfn.ru/orfey-128/" },
{ name = "Bayern 4 Klassik", url = "mms://gffstream-w8a.wm.llnwd.net/gffstream_w8a" },
{ name = "SwissRadio Küsnacht, Swiss", url = "http://www.swissradio.ch/streams/6034.asx" },
{ name = "Venice Classic Radio ITALIA", url = "http://www.veniceclassicradio.eu/live1/128.asx" },
{ name = "SwissRadio Küsnacht, Swiss Opera", url = "http://www.swissradio.ch/streams/6060.asx" },
{ name = "Radio Darvish Classical Persian", url = "http://207.200.96.228:8078/" },
{ name = "WGBH Boston USA", url = "http://streams.wgbh.org:8006/" },
{ name = "radio spivakov   russia", url = "http://radio.corbina.ru:8229/" },
{ name = "RTVE3  &#9774;&#9774; Cuando los elefantes sueñan con la música", url = "http://195.10.10.210/rtve/radio3.mp3" },
{ name = "Radio Suisse Classique", url = "http://www.radiosuisseclassique.ch/live/mp3.m3u" },
{ name = "Denmark dr.dk", url = "http://www.dr.dk/netradio/Metafiler/ASX/DR_P2_128.asx" },
{ name = "Austria RadioStephansdom", url = "http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u" },
{ name = "France Musique", url = "http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u" },
{ name = "Espana Radio Clasica", url = "http://radioclasica.rtve.stream.flumotion.com/rtve/radioclasica.mp3.m3u" },
{ name = "Slovak Radio Klasika", url = "http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u" },
{ name = "Slovak Radio Devin", url = "http://live.slovakradio.sk:8000/Devin_256.mp3.m3u" },
{ name = "Sverige-Sweden 1", url = "http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls" },
{ name = "Sverige-Sweden 2", url = "http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls" },
{ name = "Czech classic", url = "http://www.play.cz/radio/classic128.asx" },
{ name = "Latvia", url = "http://82.135.234.195/Klasika.asx" },
{ name = "BBC Radio3 192kbps", url = "http://bbc.co.uk/radio/listen/live/r3.asx" },
{ name = "P2 musik Sverige-Sweden", url = "http://http-live.sr.se/p2musik-aac-192" },
{ name = "Deutschland MDR Figaro", url = "http://avw.mdr.de/livestreams/mdr_figaro_live_128.m3u" },
{ name = "Deutschland MDR Klassik", url = "http://avw.mdr.de/livestreams/mdr_klassik_live_128.m3u" },
{ name = "&#1050;&#1083;&#1072;&#1089;&#1089;&#1080;&#1095;&#1077;&#1089;&#1082;&#1072;&#1103; &#1084;&#1091;&#1079;&#1099;&#1082;&#1072; MyRadio.com.ua  ", url = "http://music.myradio.com.ua:8000/Classica128.ogg" },
{ name = "Finland rondofm", url = "mms://mms.rondofm.fi/RondoHF" },
{ name = "Belgium RTBF Musiq 3 French-Speaking", url = "http://streaming.rtbf.be:8000/mus3128xrtbf.m3u" },
{ name = "Estonia Klassikaraadio", url = "http://web.mmm.elion.ee/klassikaraadio.asx" },
{ name = "nrk radio klassik classical station from norway", url = "http://lyd.nrk.no/nrk_radio_kl..." },
{ name = "Klasycznie Polskie Radio", url = "http://91.121.92.167:8900" },
{ name = "RNE radio Clasica Espana", url = "http://radioclasica.rtve.strea..." },
{ name = "Danmark Radio P2", url = "http://www.dr.dk/netradio/Meta..." },
{ name = "Sverige Radio P2", url = "http://http-live.sr.se/p2musik..." },
{ name = "bbc radio3 192 kbps", url = "http://bbc.co.uk/radio/listen/..." },
{ name = "Russia", url = "http://music.myradio.com.ua:8000/Classica128.ogg" },
{ name = "Finland", url = "mms://mms.rondofm.fi/RondoHF"},
{ name = "France Musique", url = "http://www.tv-radio.com/statio..."},

}
 
function descriptor()
    return { title = "Streaming Radio Player" ;
             version = "0.1" ;
             author = "Ben Dowling" ;
             capabilities = {} }
end
 
function activate()
    dlg = vlc.dialog("Streaming Radio Player")
    list = dlg:add_list(1, 3, 4, 1)
    button_play = dlg:add_button("Play", click_play, 1, 4, 4, 1)
    -- Add the radio stations
    for idx, details in ipairs(stations) do
        list:add_value(details.name, idx)
    end
    dlg:show()
end
 
function click_play()
    selection = list:get_selection()
    if (not selection) then return 1 end
    local sel = nil
    for idx, selectedItem in pairs(selection) do
        sel = idx
        break
    end
    details = stations[sel]
 
 -- Play the selected radio station
 vlc.playlist.clear()
 vlc.playlist.add({{path = details.url; title = details.name; name = details.name}})
 vlc.playlist.play()
end
 
function deactivate()
end
 
function close()
    vlc.deactivate()
end





Then launch vlc go in the view menu and it is the last item (view streaming radio player).

I have to clean the station list since i have repetitions and some do not work anymore. But most are  ok.

---

### Post by bretonfou on 2012-12-25
Oh crap i use VLC 2.0.3 ;-(

---

### Post by mc4man on 2012-12-25
Are you using the orig. from link or something like this in or about line 75
```
	-- Play the selected radio station
	vlc.playlist.clear()
	vlc.playlist.add({{path = details.url; title = details.name; name = details.name}})
	vlc.playlist.play()
end
```

Assuming you checked the debug?
(for something like this I usually start vlc normally then open the messages window & up the verbosity to 2, then start action in question

---

### Post by andrew.46 on 2012-12-25
Indeed the altered lines did the trick. Why did both of you get the working version and I scooped up the dud?

---

### Post by mc4man on 2012-12-25
> **andrew.46 said:**
> Indeed the altered lines did the trick. Why did both of you get the working version and I scooped up the dud?
Well I guess you'd need to ask our friend shantiq, either he edited his orig. posted script or the one on the weblink was edited, the last time I wanted the basic script on a new install I just copied from the recently closed thread.

---

### Post by andrew.46 on 2012-12-25
> **mc4man said:**
> Well I guess you'd need to ask our friend shantiq, either he edited his orig. posted script or the one on the weblink was edited, the last time I wanted the basic script on a new install I just copied from the recently closed thread.

It all becomes clear now, thanks for pointing that out :). I would post my thanks on the old thread but as you have mentioned it has been closed...

---

### Post by shantiq on 2012-12-26
it is a mystery guys
i never changed any of the lines since i put it up [copy and paste from coderholic page]


anyway good to know it is still going in those "futuristic" versions of VLC you are on...   still on 2.0.3 here

Merry UbuntuXmas to one and all


PS  Bretonfou  super nom :]

---

### Post by bretonfou on 2012-12-26
Hey thanks for complimenting me on my name ;-)

Merry christmas too.

I think that in the original post the first code was buggy
and since i copied the last one which was correct i never got any problem.


I have a question, how do you get those streaming url.

I have been roaming the internet on radio sites and most do not give any link.

Do you do some reverse engineering ? like opening a stream with real player or something else and then watching your internet traffic / Do you use something like Jproxy to see waht server is called and what protocol is used?

I would like to get more radio stations and to contribute a bit ;-)

---

### Post by shantiq on 2012-12-27
this [**here**]("http://www.listenlive.eu/") for example


right click on one of those kbps stations and save linked content as

[ATTACH]229195[/ATTACH]


then open in text editor and copy address


voila:KS

---

### Post by shantiq on 2012-12-29
been playing with my list a bit   [mostly european classical but not exclusively]
[nothing less than 128k]


```

--[[
 Streaming Radio Player extension for VLC &gt;= 1.1.0
 Authors: Ben Dowling (http://www.coderholic.com)
--]]
 
stations = {
	

{ name = "&#9679; BBC Radio3 HD", url = "http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls" },
{ name = "&#9679; Norway Radio Klassisk 192", url = "http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h" },
{ name = "&#9679; Radio Mozart", url = "http://listen.radionomy.com/radio-mozart.m3u" },
{ name = "&#9775; Poland Classical", url = "http://91.121.92.167:8900" },
{ name = "&#9775; VIRGIN RADIO. 104,5 RHODES GREECE", url = "http://174.36.237.66:9292/" },
{ name = "&#9775; KUHF_Classical USA", url = "http://129.7.48.200/KUHF_Classical_Hifi" },
{ name = "Rete Toscana Classica Firenze Italia", url = "mms://streaming.intoscana.it/wmtencoder/rtc.wma" },
{ name = "&#9679; CatClàssica Barcelona Catalunya", url = "mms://tv3catwmlive.fplive.net/tv3cat-live/stream_CatClassica_WM?origin=extern" },
{ name = "ABC ClassicFM", url = "http://shoutmedia.abc.net.au:10322/" },

{ name = "Klara Belgium", url = "http://mp3.streampower.be/klara-high" },


{ name = "&#9770; Classical Persian http://www.iranianradio.com/#", url = "http://213.73.255.244:10700" },
{ name = "&#9770; Radio Darvish Classical Persian", url = "http://207.200.96.228:8078/" },
{ name = "&#10026;&#10026; Radio-Orfei RUSSIA", url = "mms://live.rfn.ru/orfey-128/" },
{ name = "Bayern 4 Klassik", url = "mms://gffstream-w8a.wm.llnwd.net/gffstream_w8a" },
{ name = "SwissRadio Küsnacht, Swiss", url = "http://www.swissradio.ch/streams/6034.asx" },
{ name = "Venice Classic Radio ITALIA", url = "http://www.veniceclassicradio.eu/live1/128.asx" },
{ name = "SwissRadio Küsnacht, Swiss Opera", url = "http://www.swissradio.ch/streams/6060.asx" },

{ name = "WGBH Boston USA", url = "http://streams.wgbh.org:8006/" },
{ name = "radio spivakov   russia", url = "http://radio.corbina.ru:8229/" },
{ name = "RTVE3  &#9774;&#9774; Cuando los elefantes sueñan con la música", url = "http://195.10.10.210/rtve/radio3.mp3" },
{ name = "Radio Suisse Classique", url = "http://www.radiosuisseclassique.ch/live/mp3.m3u" },
{ name = "Denmark dr.dk", url = "http://www.dr.dk/netradio/Metafiler/ASX/DR_P2_128.asx" },
{ name = "Austria RadioStephansdom", url = "http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u" },
{ name = "France Musique", url = "http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u" },
{ name = "Espana Radio Clasica", url = "http://radioclasica.rtve.stream.flumotion.com/rtve/radioclasica.mp3.m3u" },
{ name = "Slovak Radio Klasika", url = "http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u" },
{ name = "Slovak Radio Devin", url = "http://live.slovakradio.sk:8000/Devin_256.mp3.m3u" },
{ name = "Sverige-Sweden 1", url = "http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls" },
{ name = "Sverige-Sweden 2", url = "http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls" },
{ name = "Czech classic", url = "http://www.play.cz/radio/classic128.asx" },
{ name = "Latvia", url = "http://82.135.234.195/Klasika.asx" },
{ name = "BBC Radio3 192kbps", url = "http://bbc.co.uk/radio/listen/live/r3.asx" },
{ name = "P2 musik Sverige-Sweden", url = "http://http-live.sr.se/p2musik-aac-192" },
{ name = "Deutschland MDR Figaro", url = "http://avw.mdr.de/livestreams/mdr_figaro_live_128.m3u" },
{ name = "Deutschland MDR Klassik", url = "http://avw.mdr.de/livestreams/mdr_klassik_live_128.m3u" },
{ name = "&#1050;&#1083;&#1072;&#1089;&#1089;&#1080;&#1095;&#1077;&#1089;&#1082;&#1072;&#1103; &#1084;&#1091;&#1079;&#1099;&#1082;&#1072; MyRadio.com.ua  ", url = "http://music.myradio.com.ua:8000/Classica128.ogg" },
{ name = "Finland rondofm", url = "mms://mms.rondofm.fi/RondoHF" },
{ name = "Belgium RTBF Musiq 3 French-Speaking", url = "http://streaming.rtbf.be:8000/mus3128xrtbf.m3u" },
{ name = "Estonia Klassikaraadio", url = "http://web.mmm.elion.ee/klassikaraadio.asx" },



}
 
function descriptor()
    return { title = "Streaming Radio Player" ;
             version = "0.1" ;
             author = "Ben Dowling" ;
             capabilities = {} }
end
 
function activate()
    dlg = vlc.dialog("Streaming Radio Player")
	list = dlg:add_list(1, 3, 4, 1)
	button_play = dlg:add_button("Play", click_play, 1, 4, 4, 1)
	-- Add the radio stations
    for idx, details in ipairs(stations) do
        list:add_value(details.name, idx)
    end
    dlg:show()
end
 
function click_play()
    selection = list:get_selection()
    if (not selection) then return 1 end
    local sel = nil
    for idx, selectedItem in pairs(selection) do
        sel = idx
        break
    end
    details = stations[sel]
 
	-- Play the selected radio station
	vlc.playlist.clear()
	vlc.playlist.add({{path = details.url; title = details.name; name = details.name}})
	vlc.playlist.play()
end
 
function deactivate()
end
 
function close()
    vlc.deactivate()
end
```





trying to locate 2 extra stations which look promising
only thing is i do not see where the addresses pop up


any of you "learned" boys and girls see the obvious [and if so could u please share know how]

stations are:  

```
http://culturafm.cmais.com.br/
http://www.rtp.pt/radios/online/vivace/
```

---

### Post by ron999 on 2012-12-29
> **shantiq said:**
> ```
http://www.rtp.pt/radios/online/vivace/
```
could u please share know how

This is an rtmp stream. (Though there may alternative streams available)
To listen live with VLC:-
```
rtmpdump -r "rtmp://h2j2.rtp.pt/liveradio" -a "liveradio" -W "http://www.rtp.pt/play/player.swf" -p "http://www.rtp.pt/popups/radio-vivace" -y "vivace80a" -v -o - | vlc - --meta-title "Radio Vivace"
```

(You learned how to do this at stream-recorder forum)

And the feed for the Brazil station:-
```
rtmpdump -r "rtmp://200.136.27.12/live" -a "live" -W "http://www.culturabrasil.com.br/swf/playerControleRemoto.swf" -p "http://www.culturabrasil.com.br/controle-remoto?start=fm" -y "radiofm" -v -o - | vlc - --meta-title "Radio Cultura"
```

---

### Post by shantiq on 2012-12-29
thank you Ron

these work from terminal and very well thank you

but not in the gui or am i not not loading it up right?


PS  excellent with vlc as can be recorded with red button
or piping to cvlc instead makes it invisible

---

### Post by ron999 on 2012-12-29
> **shantiq said:**
> ... but not in the gui...
Works OK here.:P

---

### Post by shantiq on 2012-12-29
oh i see...   yes works too here but cannot be started **from** the gui is what i mean,,,,    anyway brilliant will set aliases and use that way with one word trigger    [but not lines i can add to my playlist that way]


------------

in terminal

> alias "Radio_Cultura_Brasil"='rtmpdump -r "rtmp://200.136.27.12/live" -a "live" -W "http://www.culturabrasil.com.br/swf/playerControleRemoto.swf" -p "http://www.culturabrasil.com.br/controle-remoto?start=fm" -y "radiofm" -v -o - | vlc - --meta-title "Radio Cultura"'   [or replace with cvlc]

return

```
gedit  ~/.bashrc
```

copy terminal text at bottom and save

```
 . ~/.bashrc
```   to refresh

now i can trigger with  ```
Radio_Cultura_Brasil
```




again thank you

---

### Post by andrew.46 on 2012-12-29
I don't have Ubuntu open in front of me at the moment (in fact I am at work using Windows XP!) but I have a dim memory of the default ~/.bashrc with Ubuntu having a *source* section for bash aliases? I have always meant to remove my own aliases from ~/.bashrc to a separate file...

---

### Post by andrew.46 on 2012-12-30
And a New Years Eve gift from down under:

```

{ name = "ABC ClassicFM", url = "http://www.abc.net.au/res/streaming/audio/aac/classic_fm.pls" },

```

:)

---

### Post by shantiq on 2012-12-30
> **andrew.46 said:**
> And a New Years Eve gift from down under:

```

{ name = "ABC ClassicFM", url = "http://www.abc.net.au/res/streaming/audio/aac/classic_fm.pls" },

```

:)



thanx corker... i shall add to my list
Best wishes to you and to all:)

---

### Post by Ron_ on 2013-02-16
Much obliged to all for providing the links.  Here's one of my favorites: AVRO Klassiek Baroque - Hilversum, Netherlands.

[http://icecast.omroep.nl/radio4-baroque-bb-mp3](http://icecast.omroep.nl/radio4-baroque-bb-mp3)

By the way, I still use audacious as my default player.  Karmic never  rose above 98% functionality (IMHO) on my machine, so I had no  inclination to upgrade.  I notice that very few stations (e.g.,  [http://streaming.rtbf.be:8000/mus3128xrtbf.m3u](http://streaming.rtbf.be:8000/mus3128xrtbf.m3u)) will not play through  audacious, so I use Exaile or Totem as secondary players.  (Makes me a  dinosaur, I'm sure.)

---

### Post by shantiq on 2013-02-16
256 kbps nice:KS;)

a few more Dutch stations [**here**]("http://www.listenlive.eu/netherlands.html") and european here

---

### Post by shantiq on 2013-02-16
**Radios from **[Listenlive.eu]("http://Listenlive.eu")  or [shoutcast]("http://www.shoutcast.com/radio/Classical")
or if like me you are an audiophile and favour high bitrates up to 320k
the following links will delight you
[SIZE=1]
> 
[URL="http://radiobit.50webs.com/"]http://radiobit.50webs.com/
[/URL][URL="http://www.head-fi.org/t/255379/high-bitrate-internet-radio"]http://www.head-fi.org/t/255379/high-bitrate-internet-radio
[/URL][URL="http://stream.psychomed.gr/streams.html"]http://stream.psychomed.gr/streams.html
[/URL][http://www.linn.co.uk/music#radio](http://www.linn.co.uk/music#radio)


[/SIZE]

[[IMG]http://img15.imageshack.us/img15/4976/8ded.th.png[/IMG]]("http://img15.imageshack.us/img15/4976/8ded.png")




=======================


This is mostly all classical apart from the ones marked with &#9775; are Ambient/Relaxation and [COLOR=#000000][I]&#9770; classical iranian and turkish
[/I][/COLOR][SIZE=1]
Based on info mostly from [shoutcast.com]("http://www.shoutcast.com/") and [listenlive.eu]("http://www.listenlive.eu/") 
[Links may need to be updated from time to time]
[SIZE=1]
[/SIZE][obviously remove and add entries to suit your musical interests]

&#9679; on listenlive.eu to find url of actual station  [right-click on where it says kbps/save link as/open in text editor and find url][/SIZE]
[SIZE=1]&#9679; on shoutcast to find url of actual station  [right-click on play button to save link as/open in text editor and find url]
[/SIZE]

> [noparse]





--[[
Streaming Radio Player extension for VLC &gt;= 1.1.0
Authors: Ben Dowling ([http://www.coderholic.com](http://www.coderholic.com))


List Compiled by Shantiq
Mostly European Classical also Ambient and Classical Iranian


Based on info mostly from ([http://www.shoutcast.com/](http://www.shoutcast.com/)) and ([http://www.listenlive.eu/](http://www.listenlive.eu/)) 
[Links may need to be updated from time to time]




--]]


stations = {




--[[high kbps first on this list]]--




{ name = "&#9679; BBC Radio3 HD", url = "http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls" },
{ name = "&#9679; Norway Radio Klassisk 192", url = "http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h" },
{ name = "Linn Classical 320k", url = "http://89.16.185.174:8003/stream" },
--[[[http://www.linn.co.uk/music#radio]]--](http://www.linn.co.uk/music#radio]]--)
{ name = "Audiophile Jazz 320k", url = "http://50.7.173.162:2199/tunein/jazz.pls" },
{ name = "Audiophile Baroque 320k", url = "http://50.7.173.162:2199/tunein/baroque.pls" },
{ name = "Audiophile Classical 320k", url = "http://50.7.173.162:2199/tunein/classical.pls" },
{ name = "Audiophile Live 320k", url = "http://50.7.173.162:2199/tunein/live.pls" },
--[[[http://stream.psychomed.gr/streams.html]]--](http://stream.psychomed.gr/streams.html]]--)
{ name = "WBAA Purdue University Indiana [256k]", url = "http://audio-new.wbaa.purdue.edu:8000/wbaa-fm" },
--[[[http://wbaa.org/]]--](http://wbaa.org/]]--)
{ name = "&#9679; Hamburg - Klassik Radio Brazil", url = "http://62.27.47.224:8000/klassikradiobrazil128/livestream.mp3" },


{ name = "&#9679; Poland - Radio Chopin", url = "http://zetcho-02.cdn.eurozet.pl:8410/" },






--[[PROG]]--


{ name = "&#10054; &#10012;acidbarrett", url = "http://streaming.radionomy.com/acidbarrett" },
{ name = "&#10054; &#10012;Progrock.com", url = "http://174.37.16.73:1320/Live" },
{ name = "&#10054; &#10012;Purple Piper Progressive Rock", url = "http://95.141.45.144:8036" },
{ name = "&#10054; &#10012;Radio Floyd", url = "http://streaming.radionomy.com/radio-floyd" },
{ name = "&#10054; &#10012;pinkfloydteguz", url = "http://streaming.radionomy.com/pinkfloydteguz" },








{ name = "&#9679; Radio Mozart", url = "http://listen.radionomy.com/radio-mozart.m3u" },
{ name = "&#9679; Poland Classical", url = "http://91.121.92.167:8900" },
{ name = "&#9679; FIP [128k]", url = "http://mp3.live.tv-radio.com/fip/all/fiphautdebit.mp3" },
{ name = "&#9679; KUHF_Classical USA", url = "http://129.7.48.200/KUHF_Classical_Hifi" },
{ name = "&#9679; Rete Toscana Classica Firenze Italia", url = "mms://streaming.intoscana.it/wmtencoder/rtc.wma" },


{ name = "&#9679; ARS NOVA -Early Music Poland", url = "http://37.59.8.151:8200" },
{ name = "&#9679; SRR Radio România Muzical", url = "http://stream2.srr.ro:8022/" },
{ name = "&#9679;&#9770; Türkiye &#304;TÜ Radyosu Klasik", url = "http://160.75.86.29:8097/" },


{ name = "&#9679; Northern Cyprus Bayrak Klasik", url = "http://sc.brtk.net:8006/" },


{ name = "ABC ClassicFM", url = "http://www.abc.net.au/res/streaming/audio/mp3/classic_fm.pls" },
--[[ only in 96k max--]]
{ name = "KEXP Seattle", url = "http://live-mp3-128.kexp.org:8000/" },
{ name = "Klara Belgium", url = "http://mp3.streampower.be/klara-high" },
{ name = "Holland &#9679; AVRO Baroque around the clock", url = "http://icecast.omroep.nl/radio4-baroque-bb-mp3" },
{ name = "Holland &#9679; AVRO De Klassiek 24/7", url = "http://icecast.omroep.nl:80/radio4-klassieken-bb-mp3" },
{ name = "Ukraine &#9679; MyRadio Classical music", url = "http://music.myradio.ua:8000/Classica128.ogg" },
{ name = "Bulgaria &#9679; Classic FM", url = "http://live.btvradio.bg:8000/classic-fm.mp3" },
{ name = "Denmark &#9679; dr.dk", url = "http://live-icy.gss.dr.dk:8000/A/A04H.mp3" },
{ name = "Denmark &#9679; Radio Klassisk", url = "http://onair.100fmlive.dk:80/klassisk_live.mp3" },
{ name = "France &#9679; Radio Classique 128k", url = "http://broadcast.infomaniak.net:80/radioclassique-high.mp3" },
{ name = "France Musique", url = "http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u" },


{ name = "Jazz &#9679; &#268;Ro Jazz Prague Czech Republic", url = "http://stream3.rozhlas.cz:8000/jazz_high.ogg" },
{ name = "Jazz &#9679; tsfjazz France", url = "http://tsfjazz.ice.infomaniak.ch:80/tsfjazz-high" },
{ name = "&#9775;ToxicNet Tunes", url = "http://64.64.215.118:6101/playlists\main.lst" },
{ name = "&#9775;Zen Radio", url = "http://www.zenradio.fm/" },
{ name = "&#9775;ELDORADIO - Chill Channel", url = "http://sc-chill.eldoradio.lu:80/" },
{ name = "&#9775;Nirvana Radio - Music for Meditation and Relaxation", url = "http://174.142.192.209:9022" },
{ name = "&#9775;OCEAN WAVES AMBIENT", url = "http://174.142.192.209:9022" },
{ name = "&#9775;Nirvana Ambient Radio - The Best Ambient Music", url = "http://81.219.54.6:8002" },
{ name = "&#9775;Chroma Ambient", url = "http://69.70.125.26:100" },
{ name = "&#9775;Dub Lubin Radio : Zen Mantra - Live Meditation", url = "http://69.70.125.26:100" } ,
{ name = "&#9775;Radio Sri Chinmoy - spiritual music for meditation 192k", url = "http://96.126.107.232:8000/" } ,
{ name = "&#9775;Groove Salad [SomaFM]", url = "http://173.192.176.180:8032" } ,
{ name = "&#9775;&#9775;Ambient Sleeping Pill", url = "http://173.236.50.59:80" } ,
{ name = " &#9775;Ibiza Digital Labs - Relax Music from Ibiza(Chillout,Lounge,Ambient)", url = "http://50.7.98.106:8695" } ,




{ name = "&#9775;.POLSKASTACJA .PL ))) EDEN (New Age & World Music) (Polskie Radio)", url = "http://91.121.89.153:9900" },
{ name = "&#9770; Radio Golha Persian", url = "mms://84.244.130.224:3737/radiogolha_bk" },
{ name = "&#9770; Kral FM Istanbul[128Kbps]Turkish Arabesque music", url = "http://46.20.3.204:80/" },
{ name = "&#9770; Classical Persian http://www.iranianradio.com/#", url = "http://213.73.255.244:10700/" },
{ name = "&#9770; Radio Darvish Classical Persian", url = "http://78.129.190.50:8037/" },




{ name = "&#9770; CALMRADIO.COM - PERSIA", url = "http://206.190.129.220:11808" },
{ name = "&#10026;&#10026; Radio-Orfei RUSSIA", url = "mms://live.rfn.ru/orfey-128/" },
{ name = "Bayern 4 Klassik", url = "http://gffstream.ic.llnwd.net/stream/gffstream_w13a" },
{ name = "SwissRadio Küsnacht, Swiss", url = "http://www.swissradio.ch/streams/6034.asx" },
{ name = "Venice Classic Radio ITALIA", url = "http://www.veniceclassicradio.eu/live1/128.asx" },
{ name = "SwissRadio Küsnacht, Swiss Opera", url = "http://www.swissradio.ch/streams/6060.asx" },
{ name = "WGBH Boston USA", url = "http://streams.wgbh.org:8006/" },
{ name = "RTVE3 &#9774;&#9774; Cuando los elefantes sueñan con la música 15H00", url = "http://195.10.10.226/rtve/radio3.mp3" },


{ name = "Radio Suisse Classique", url = "http://www.radiosuisseclassique.ch/live/mp3.m3u" },
{ name = "Austria RadioStephansdom", url = "http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u" },
{ name = "Espana Radio Clasica", url = "http://radioclasica.rtve.stream.flumotion.com/rtve/radioclasica.mp3.m3u" },
{ name = "Slovak Radio Klasika", url = "http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u" },
{ name = "Slovak Radio Devin", url = "http://live.slovakradio.sk:8000/Devin_256.mp3.m3u" },
{ name = "Sverige-Sweden 1", url = "http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls" },
{ name = "Sverige-Sweden 2", url = "http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls" },
{ name = "Czech classic", url = "http://www.play.cz/radio/classic128.asx" },
{ name = "Latvijas Radio 3 Klasika", url = "mms://lr1w.latvijasradio.lv/pplr3" },
{ name = "BBC Radio3 192kbps", url = "http://bbc.co.uk/radio/listen/live/r3.asx" },
{ name = "P2 musik Sverige-Sweden", url = "http://http-live.sr.se/p2musik-aac-192" },
{ name = "Deutschland MDR Figaro", url = "http://avw.mdr.de/livestreams/mdr_figaro_live_128.m3u" },
{ name = "Deutschland MDR Klassik", url = "http://avw.mdr.de/livestreams/mdr_klassik_live_128.m3u" },
{ name = "&#1050;&#1083;&#1072;&#1089;&#1089;&#1080;&#1095;&#1077;&#1089;&#1082;&#1072;&#1103; &#1084;&#1091;&#1079;&#1099;&#1082;&#1072; MyRadio.com.ua ", url = "http://music.myradio.com.ua:8000/Classica128.ogg" },
{ name = "Finland rondofm", url = "http://stream.iradio.fi:8000/klasu-hi.mp3" },
{ name = "Finland YLE Ylen Klassinen", url = "mms://mediau.yle.fi/liveklassinen" },
{ name = "Finland Classic", url = "http://stream.radioclassic.fi:8000/stream/1/" },
{ name = "Belgium RTBF Musiq 3 French-Speaking", url = "http://broadcast.infomaniak.net:80/musiq3-128.mp3" },
{ name = "Estonia Klassikaraadio", url = "http://icecast.err.ee:80/klassikaraadio.mp3" },
{ name = "&#9679; KPFK 90.7 FM [Los Angeles]&#9775; ", url = "http://sc1.mainstreamnetwork.com:9042/" },


}








function descriptor()
return { title = "Streaming Radio Player" ;
version = "0.1" ;
author = "Ben Dowling" ;
capabilities = {} }
end








function activate()
dlg = vlc.dialog("Streaming Radio Player")
list = dlg:add_list(1, 3, 4, 1)
button_play = dlg:add_button("Play", click_play, 1, 4, 4, 1)
-- Add the radio stations
for idx, details in ipairs(stations) do
list:add_value(details.name, idx)
end
dlg:show()
end








function click_play()
selection = list:get_selection()
if (not selection) then return 1 end
local sel = nil
for idx, selectedItem in pairs(selection) do
sel = idx
break
end
details = stations[sel]








-- Play the selected radio station
vlc.playlist.clear()
vlc.playlist.add({{path = details.url; title = details.name; name = details.name}})
vlc.playlist.play()
end








function deactivate()
end








function close()
vlc.deactivate()
end


[/noparse]



**just to recap on how to use**


**1&#9679;**  copy and paste above text as classical.lua    save in home folder

you may then need to create lua folder and extensions folder too:
```
cd ~/.local/share/vlc/ ; mkdir lua ; cd ~/.local/share/vlc/lua ; mkdir extensions

```


**2&#9679; **then to move to right place
```
sudo mv classical.lua ~/.local/share/vlc/lua/extensions
```

**3&#9679;**   go to vlc/view/ streaming radio player

**4&#9679; **  to edit list   ```
sudo gedit ~/.local/share/vlc/lua/extensions/classical.lua
```
and make your changes/additions etc

[[IMG]http://img15.imageshack.us/img15/4976/8ded.th.png[/IMG]]("http://img15.imageshack.us/img15/4976/8ded.png")


to get back here enter in search:
 &#9658;    "classical.lua"  or    "Arabesque"


also can be turned into a pls file see [here]("http://ubuntuforums.org/showthread.php?t=2175955&p=12796523#post12796523")

---

### Post by andrew.46 on 2013-02-19
> **Ron_ said:**
>  I notice that very few stations (e.g.,  [http://streaming.rtbf.be:8000/mus3128xrtbf.m3u](http://streaming.rtbf.be:8000/mus3128xrtbf.m3u)) will not play through  audacious, so I use Exaile or Totem as secondary players.  (Makes me a  dinosaur, I'm sure.)

Oddly enough this plays fine with Audacious for me although a little laggy from this end of the world....

---

### Post by shantiq on 2013-10-08
i just updated the list  of classical stations i compiled earlier...    links change from time to time

[here is]("http://ubuntuforums.org/showthread.php?t=2098167&p=12512918#post12512918") the up-to-date version  ...   still all 128k or higher

---

