---
title: "How to set up a really good radio player on VLC"
date: 2013-10-11
forum: Multimedia Software
---

### Post by shantiq on 2013-10-11
[B][FONT=century gothic][SIZE=1]NB: This is also elsewhere on the forum but i have "refurbished it" and thought it might be of interest to "new" visitors to the site    ALL THE CODE HERE is the handiwork of [Ben Dowling]("http://www.coderholic.com/extending-vlc-with-lua/")
[/SIZE]
[/FONT]
Radios from [/B][Listenlive.eu]("http://listenlive.eu/") or [shoutcast]("http://www.shoutcast.com/radio/Classical")
or if like me you are an audiophile and favour high bitrates up to 320k and even one Flac
the following links will delight you
[SIZE=1]
> 
[SIZE=1][URL="http://radio.cesnet.cz:8000/cro-d-dur.flac"]http://radio.cesnet.cz:8000/cro-d-dur.flac
[/URL][/SIZE][URL="http://radiobit.50webs.com/"]http://radiobit.50webs.com/
[/URL][URL="http://www.head-fi.org/t/255379/high-bitrate-internet-radio"]http://www.head-fi.org/t/255379/high-bitrate-internet-radio
[/URL][URL="http://stream.psychomed.gr/streams.html"]http://stream.psychomed.gr/streams.html
[/URL][http://www.linn.co.uk/music#radio](http://www.linn.co.uk/music#radio)


[/SIZE]

[IMG]http://s20.postimg.org/5vm1v6v4t/lua.png[/IMG]

[B][SIZE=1]seen here on vlc 2.1.5 Rincewind
[/SIZE][/B]

=======================


This is mostly all classical apart from the ones marked with &#9775; are Ambient/Relaxation and [COLOR=#000000][I]&#9770; classical iranian and turkish
[/I][/COLOR][SIZE=1]
Based on info mostly from [shoutcast.com]("http://www.shoutcast.com/") and [listenlive.eu]("http://www.listenlive.eu/") 
[Links may need to be updated from time to time]
[SIZE=1]
[/SIZE][obviously remove and add entries to suit your musical interests]

&#9679; on listenlive.eu to find url of actual station [right-click on where it says kbps/save link as/open in text editor and find url][/SIZE]
[SIZE=1]&#9679; on shoutcast to find url of actual station [right-click on play button to save link as/open in text editor and find url]
[/SIZE]

> [noparse]
--[[
Streaming Radio Player extension for VLC &gt;= 1.1.0
Authors: Ben Dowling (http://www.coderholic.com)




List Compiled by Shantiq
Mostly European Classical also Ambient and Classical Iranian and a few odds and sods




Based on info mostly from ([http://www.shoutcast.com/](http://www.shoutcast.com/)) and ([http://www.listenlive.eu/](http://www.listenlive.eu/)) 
[Links may need to be updated from time to time] --]]








stations = {




--[[
high specs first
]]--








{ name = "&#9679; Czech Classical D-dur [Flac]", url = "http://radio.cesnet.cz:8000/cro-d-dur.flac" },
--[[[http://www.rozhlas.cz/d-dur/portal/](http://www.rozhlas.cz/d-dur/portal/) --]]
{ name = "&#9679; BBC Radio3 HD", url = "http://bbcmedia.ic.llnwd.net/stream/bbcmedia_lc1_radio3_q?s=1435031090&e=1435045490&h=89ca02cc9bfb44fd4f7d646489833d46" },
{ name = "&#9679; Norway Radio Klassisk 192", url = "http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h" },
{ name = "Linn Classical 320k", url = "http://89.16.185.174:8003/stream" },
{ name = "Audiophile Jazz 320k", url = "http://50.7.173.162:2199/tunein/jazz.pls" },
{ name = "Audiophile Baroque 320k", url = "http://50.7.173.162:2199/tunein/baroque.pls" },
{ name = "Audiophile Classical 320k", url = "http://50.7.173.162:2199/tunein/classical.pls" },
{ name = "Audiophile Live 320k", url = "http://50.7.173.162:2199/tunein/live.pls" },
--[[[http://stream.psychomed.gr/streams.html](http://stream.psychomed.gr/streams.html)--]]
{ name = "&#9679; Hamburg - Klassik Radio Brazil", url = "http://62.27.47.224:8000/klassikradiobrazil128/livestream.mp3" },
{ name = "&#9679; Poland - Radio Chopin", url = "http://zetcho-02.cdn.eurozet.pl:8410/" },
{ name = "&#9679; BBC Radio 6", url = "http://www.bbc.co.uk/radio/listen/live/r6_aaclca.pls" },
{ name = "&#9679; Moldova - &#1056;&#1091;&#1089;&#1089;&#1082;&#1086;&#1077; &#1056;&#1072;&#1076;&#1080;&#1086; 103.7 [Russian Top 40]", url = "http://89.28.86.142:7030/live" },






{ name = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;", url = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;" }, --[[THIS HERE IS A PARTITION]]--




--[[
US and Oz Classical
]]--








{ name = "KEXP Seattle", url = "http://live-mp3-128.kexp.org:8000/" },
{ name = "WBAA Purdue University Indiana [256k]", url = "http://audio-new.wbaa.purdue.edu:8000/wbaa-fm" },
{ name = "WKSU OHIO", url = "http://66.225.205.8:8030/" },
{ name = "TUCSON ARIZONA CLASSICAL", url = "http://streaming.azpm.org:80/kuat192.mp3" },
{ name = "WGBH Boston USA", url = "http://streams.wgbh.org:8006/" },
{ name = "ABC ClassicFM", url = "http://www.abc.net.au/res/streaming/audio/mp3/classic_fm.pls" },
{ name = "ABC Classic 2", url = "http://mfile.akamai.com/112897/live/reflector:56577.asx?bkup=56576" },




{ name = "&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;", url = "&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;" }, --[[THIS HERE IS A PARTITION]]--





{ name = "&#9679; SRR Radio România Muzical", url = "http://stream2.srr.ro:8022/" },
{ name = "&#9679; Northern Cyprus Bayrak Klasik", url = "http://sc.brtk.net:8006/" },








{ name = "Klara Belgium", url = "http://mp3.streampower.be/klara-high" },
{ name = "Holland &#9679; AVRO Baroque around the clock", url = "http://icecast.omroep.nl/radio4-baroque-bb-mp3" },
{ name = "Holland &#9679; AVRO De Klassiek 24/7", url = "http://icecast.omroep.nl:80/radio4-klassieken-bb-mp3" },
{ name = "Ukraine &#9679; MyRadio Classical music", url = "http://music.myradio.ua:8000/Classica128.ogg" },
{ name = "Bulgaria &#9679; Classic FM", url = "http://live.btvradio.bg:8000/classic-fm.mp3" },
{ name = "Denmark &#9679; dr.dk", url = "http://live-icy.gss.dr.dk:8000/A/A04H.mp3" },
{ name = "Denmark &#9679; Radio Klassisk", url = "http://onair.100fmlive.dk:80/klassisk_live.mp3" },
{ name = "France &#9679; Radio Classique 128k", url = "http://broadcast.infomaniak.net:80/radioclassique-high.mp3" },
{ name = "France Musique", url = "http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u" },








{ name = "&#9679; Radio Mozart", url = "http://listen.radionomy.com/radio-mozart.m3u" },
{ name = "&#9679; Poland Classical", url = "http://91.121.92.167:8900" },
{ name = "&#9679; FIP [128k]", url = "http://mp3.live.tv-radio.com/fip/all/fiphautdebit.mp3" },
{ name = "&#9679; KUHF_Classical USA", url = "http://129.7.48.200/KUHF_Classical_Hifi" },
{ name = "&#9679; Rete Toscana Classica Firenze Italia", url = "mms://streaming.intoscana.it/wmtencoder/rtc.wma" },








{ name = "&#9775;Dub Lubin Radio : Zen Mantra - Live Meditation", url = "http://69.70.125.26:100" } ,
{ name = "&#9775;Radio Sri Chinmoy - spiritual music for meditation 192k", url = "http://96.126.107.232:8000/" } ,
{ name = "&#9775;Groove Salad [SomaFM]", url = "http://173.192.176.180:8032" } ,

{ name = " &#9775;Ibiza Digital Labs - Relax Music from Ibiza(Chillout,Lounge,Ambient)", url = "http://50.7.98.106:8695" } ,
{ name = "&#9775;.POLSKASTACJA .PL ))) EDEN (New Age & World Music) (Polskie Radio)", url = "http://91.121.89.153:9900" },




{ name = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;", url = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;" },




--[[
Eastern
]]--


{ name = "&#9770; Arabesk Radyo", url = "http://37.247.101.101:5934/" },
{ name = "&#9770; RADYO KULU", url = "http://37.187.90.121:3940/" },
{ name = "&#9770; Radio Golha Persian", url = "mms://84.244.130.224:3737/radiogolha_bk" },
{ name = "&#9770; Kral FM Istanbul[128Kbps]Turkish Arabesque music", url = "http://46.20.3.204:80/" },
{ name = "&#9770; Classical Persian http://www.iranianradio.com/#", url = "http://213.73.255.244:10700/" },
{ name = "&#9770; Radio Darvish Classical Persian", url = "http://78.129.190.50:8037/" },
{ name = "&#9770; Türkiye &#304;TÜ Radyosu Klasik", url = "http://160.75.86.29:8097/" },




{ name = "&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;", url = "&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;&#50883;" }, --[[THIS HERE IS A PARTITION]]--




{ name = "&#10026;&#10026; Radio-Orfei RUSSIA", url = "mms://live.rfn.ru/orfey-128/" },
{ name = "Bayern 4 Klassik", url = "http://gffstream.ic.llnwd.net/stream/gffstream_w13a" },
{ name = "SwissRadio Küsnacht, Swiss", url = "http://www.swissradio.ch/streams/6034.asx" },
{ name = "Venice Classic Radio ITALIA", url = "http://www.veniceclassicradio.eu/live1/128.asx" },
{ name = "SwissRadio Küsnacht, Swiss Opera", url = "http://www.swissradio.ch/streams/6060.asx" },
{ name = "RTVE3 &#9774;&#9774; Cuando los elefantes sueñan con la música 15H00", url = "http://195.10.10.226/rtve/radio3.mp3" },
{ name = "Radio Suisse Classique", url = "http://www.radiosuisseclassique.ch/live/mp3.m3u" },
{ name = "Austria RadioStephansdom", url = "http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u" },
{ name = "Espana Radio Clasica", url = "http://radioclasica.rtveradio.cires21.com/radioclasica/mp3/icecast.audio" },
{ name = "Slovak Radio Klasika", url = "http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u" },
{ name = "Slovak Radio Devin", url = "http://live.slovakradio.sk:8000/Devin_256.mp3.m3u" },
{ name = "Sverige-Sweden 1", url = "http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls" },
{ name = "Sverige-Sweden 2", url = "http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls" },
{ name = "Czech classic", url = "http://icecast8.play.cz:80/classic128.mp3" },
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
{ name = "&#9679; KPFK 90.7 FM [Los Angeles]&#9775;", url = "http://sc1.mainstreamnetwork.com:9042/" },


{ name = "Jazz &#9679; &#268;Ro Jazz Prague Czech Republic", url = "http://stream3.rozhlas.cz:8000/jazz_high.ogg" },
{ name = "Jazz &#9679; tsfjazz France", url = "http://tsfjazz.ice.infomaniak.ch:80/tsfjazz-high" },

{ name = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;", url = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;" },

--[[
PROG
]]--

{ name = "&#10054; &#10012;acidbarrett", url = "http://streaming.radionomy.com/acidbarrett" },
{ name = "&#10054; &#10012;Progrock.com", url = "http://184.154.185.181:8000/" },
{ name = "&#10054; &#10012;Purple Piper Progressive Rock", url = "http://s1.shoutitaly.com:2199/tunein/purplepiper.asx" },
{ name = "&#10054; &#10012;Radio Floyd", url = "http://streaming.radionomy.com/radio-floyd" },
{ name = "&#10054; &#10012;pinkfloydteguz", url = "http://streaming.radionomy.com/pinkfloydteguz" },


{ name = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;", url = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;" },




--[[
DEVOTIONAL
]]--

{ name = "Kripalu Bhakti Radio", url = "http://68.168.101.146:8417" },
{ name = "Mantra Radio", url = "http://50.7.70.58:8435" },
{ name = "Kirtan Radio", url = "http://sc8.spacialnet.com:25872" },
{ name = "Radio Sri Chinmoy - spiritual music for meditation", url = "http://109.169.26.139:8534/stream" },
{ name = "Radio Krishna Centrale - RKC", url = "http://81.25.96.13:8090" },
{ name = "nadchathira Fm", url = "http://109.169.26.139:8534/stream" },




{ name = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;", url = "&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;&#8578;" },




--[[
NEW AGE RELAXATION
]]--




{ name = "&#9775;Zen Radio", url = "http://iradio.iceca.st:80/zenradio" },
{ name = "&#9775;ELDORADIO - Chill Channel", url = "http://sc-chill.eldoradio.lu:80/" },
{ name = "&#9775;Nirvana Radio - Music for Meditation and Relaxation", url = "http://91.121.134.15:9106" },
{ name = "&#9775;OCEAN WAVES AMBIENT", url = "http://174.142.192.209:9022" },
{ name = "&#9775;Nirvana Ambient Radio - The Best Ambient Music", url = "http://81.219.54.6:8002" },
{ name = "&#9775;Chroma Ambient", url = "http://148.251.184.14:8004" },




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



&#9658;&#9658;  **how to use **&#9658;&#9658;
=============

**First enable lua in your synaptic **then

**1&#9679;** copy and paste above text as classical.lua save in home folder



**2&#9679; **then to move to right place
```
sudo mv classical.lua /usr/lib/vlc/lua/extensions
```


**3&#9679;** go to vlc/view/ streaming radio player to view your new radio player



**4&#9679; **to edit list  ```
sudo gedit /usr/lib/vlc/lua/extensions/classical.lua
``` 

[[IMG]http://img15.imageshack.us/img15/4976/8ded.th.png[/IMG]]("http://img15.imageshack.us/img15/4976/8ded.png")


[SIZE=1][B]to get back to this page/thread enter in search:
[/B][/SIZE]&#9658; "classical.lua" or "Arabesque"


also can easily be turned into a pls file see [here]("http://ubuntuforums.org/showthread.php?t=2175955&p=12796523#post12796523")

---

### Post by andrew.46 on 2013-10-12
Thanks shan, I have scooped up your list and look forward to exploring it further!!!

---

### Post by shantiq on 2013-10-13
Andrew i was stunned to see how often they "change" their url.   Two years on 8 or 9 of them had shifted.   All up to date i think  Oct 2013.     I shall keep an eye/ear open :::]]]

---

### Post by shantiq on 2013-10-20
took about 4 minutes to install on 13.10

---

### Post by achuthpnr on 2014-01-11
Hi,
I just wanted to append my extended radio station list. The stations are classified according to their bit rate. All links are checked and found to be functional today.

-----------------------------------------------------------------------------------------

--[[
Streaming Radio Player extension for VLC &gt;= 1.1.0
Authors: Ben Dowling ([http://www.coderholic.com](http://www.coderholic.com))

List Compiled by Achu
Mostly European Classical also Ambient and Classical Iranian

[Links may need to be updated from time to time]

general format to add new stations
{ name = "xxxx", url = "xxxx" },

--]]

stations = {


{ name = "Radio Classical 91.7 [24kbps]", url = "http://pubint.ic.llnwd.net/stream/pubint_kuha" },
{ name = "Hrvatski radio [32kbps]", url = "mms://213.5.57.160/hr3" },
{ name = "KWAX [32kbps]", url = "http://184.171.104.41:8000/KWAX32.mp3" },
{ name = "WUGA FM Athens, GA, USA [32kbps]", url = "http://live.wuga.org:8002/" },
{ name = "Radio Classica [32kbps]", url = "http://radio.gruppoeditorialebresciana.it/radioclassica" },
{ name = "Radio classic99 [32kbps]", url = "http://streamhost1.classic99.org/classic99-22k" },
{ name = "BBC Radio 3 [32kbps]", url = "mms://wmlive-nonacl.bbc.net.uk/wms/bbc_ami/radio3/radio3_bb_live_int_eq1_sl0" },
{ name = "Radio Classic - czeck [32kbps]", url = "mms://netshow4.play.cz/classic" },
{ name = "KCSC FM [32kbps]", url = "mms://stream.uco.edu/wmtencoder/kcscfm.wma" },
{ name = "AutoRadio [32kbps]", url = "http://81.19.85.197/auto32.mp3" },
{ name = "Radio blago- Russian [32kbps] ", url = "mms://live.radioblago.ru:3278" },
{ name = "Latvijas Radio - LR4 [32kbps]", url = "mms://lr1w.latvijasradio.lv/pplr4" },
{ name = "France Musique [32kbps]", url = "http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-32k.m3u" },
{ name = "KPFK 90.7 FM [32kbps] [Los Angeles] ", url = "http://sc1.mainstreamnetwork.com:9042/" },
{ name = "Klara continuo | kwaliteit * [32kbps]", url = "http://mp3.streampower.be/klaracontinuo-low" },
{ name = "Klara Belgium low [32kbps]", url = "http://mp3.streampower.be/klara-low" },
{ name = "Radio Golha Persian [32kbps]", url = "mms://84.244.130.224:3737/radiogolha_bk" },


{ name = "CRo 3 - Vltava [40kbps]", url = "http://icecast5.play.cz/cro3-32.mp3" },

{ name = "CX 6 - Clasica [48kbps]", url = "http://radio.sodreuruguay.com:9090/listen.pls" },
{ name = "ROKS [48kbps]", url = "http://81.19.85.203/roks48.mp3" },
{ name = "Classical KING FM [48kbps]", url = "http://216.218.147.60:8246" },
{ name = "Classic FM uk [48kbps]", url = "http://ice-the.musicradio.com:80/ClassicFM" },
{ name = "Accent 4 [48kbps]", url = "http://str0.creacast.com:900/" },

{ name = "Radio Stephansdom [56kbps]", url = "http://str01.rdom.apa.net:8000/rsdstream56" },
{ name = "SR2 [56kbps]", url = "http://gffstream.ic.llnwd.net/stream/gffstream_mp3_w59b" },
{ name = "WBJC [56kbps]", url = "http://wbjc-sc.streamguys.org/listen.pls" },
{ name = "ToxicNet Tunes [56kbps]", url = "http://64.64.215.118:6101/playlists\main.lst" },

{ name = "Radio Classique [64kbps]", url = "http://broadcast.infomaniak.net/radioclassique-low.mp3" },
{ name = "Narodnoe Radio [64kbps]", url = "http://213.85.130.203:8080/stream.mp3" },
{ name = "SYMPHONY 92.4FM [64kbps]", url = "mms://a1339.l11459121338.c114591.g.lm.akamaistream.net/D/1339/114591/v0001/reflector:21338" },
{ name = "Classical 88.7 KCME [64kbps]", url = "http://www.kcme.org/Audio%20Players/Broadband/listen.pls" },
{ name = "Klassikaraadio [64kbps]", url = "http://klassikaraadio.err.ee/gfx/klassikaraadio64.m3u" },
{ name = "Klara continuo [64kbps]", url = "http://mp3.streampower.be/klaracontinuo-mid" },
{ name = "Klara [64kbps]", url = "http://mp3.streampower.be/klara-mid" },
{ name = "Radio ZVEZDA (Moscow) 95.6 FM [64kbps]", url = "http://81.19.85.204/zvezda64.mp3" },
{ name = "Voice of Russia [64kbps]", url = "http://rus.streamr.ru" },
{ name = "DetiFM [64kbps]", url = "http://79.143.70.114:8000/detifm-64k.mp3" },
{ name = "Dorognoe Radio [64kbps]", url = "http://81.19.85.197/dorognoe64.mp3" },

{ name = "WYSU All Classical Channel [96kbps]", url = "http://live.wysu.org:3180/hd2.m3u" },
{ name = "WRCJ 90.9 FM [96kbps]", url = "http://www.wrcjfm.org/listen.pls" },
{ name = "Classical 90.7, KVNO [96kbps]", url = "http://kvnovm-HD1.unomaha.edu:8000/listen.m3u" },
{ name = "vpubradio_kvpr [96kbps]", url = "http://vpubradio.ic.llnwd.net/stream/vpubradio_kvpr.m3u" },
{ name = "Classical Piano Trios [96kbps]", url = "http://radio.north.kz:8000/classicalpianotrios_hi" },
{ name = "Whisperings  Solo Piano Radio [96kbps]", url = "http://radio.north.kz:8000/solopiano" },
{ name = "Litradio [96kbps]", url = "http://79.137.234.183:8000" },
{ name = "Vocal New Age  [96kbps]", url = "http://pub4.sky.fm:80/sky_vocalnewage" },
{ name = "Romantica [96kbps]", url = "http://pub4.sky.fm:80/sky_romantica" },
{ name = "Ambient [96kbps]", url = "http://radio.north.kz:8000/ambient_hi" },
{ name = "Nature [96kbps]", url = "http://radio.north.kz:8000/nature_hi" },
{ name = "Nature - SKY.FM - soothing sounds of nature music! [96kbps]", url = "http://radio.north.kz:8000/nature_hi" },
{ name = "ABC ClassicFM [96kbps]", url = "http://www.abc.net.au/res/streaming/audio/mp3/classic_fm.pls" },


{ name = "Venice Classic Radio Italia [128kbps]", url = "http://174.36.206.197:8000" },
{ name = "Classical KUSC [128kbps]", url = "http://kuscstream.org/pls/kusc128.pls" },
{ name = "Swiss Internet Radio  Public Domain Classical [128kbps]", url = "http://stream2137.init7.net:80" },
{ name = "Swiss Internet Radio  Opera [128kbps]", url = "http://stream2139.init7.net:80" },
{ name = "Swiss Internet Radio  Modern Jazz [128kbps]", url = "http://stream2140.init7.net:80" },
{ name = "Bach [128kbps]", url = "http://audio.wgbh.org/otherWaysToListen/Bach.m3u" },
{ name = "Holiday [128kbps]", url = "http://audio.wgbh.org/otherWaysToListen/Holiday.m3u" },
{ name = "Jazz Decades [128kbps]", url = "http://audio.wgbh.org/otherWaysToListen/jazzDecades.m3u" },
{ name = "Kids Classical [128kbps]", url = "http://audio.wgbh.org:8110" },
{ name = "NDR Kultur [128kbps]", url = "http://www.ndr.de/resources/metadaten/audio/m3u/ndrkultur.m3u" },
{ name = "Classical Wyoming [128kbps]", url = "http://wprhqstream3.uwyo.edu:8000/kuwy.m3u" },
{ name = "TheClassicalStation.org [128kbps] ", url = "http://www.ibiblio.org/wcpe/wcpe.pls" },
{ name = "WFDD 2 [128kbps]", url = "http://live.str3am.com:2640/wfdd2.mp3.m3u" },
{ name = "WRTI FM [128kbps]", url = "http://pubint.ic.llnwd.net/stream/pubint_wrti" },
{ name = "WPRB 103.3 FM (Princeton, NJ) [128kbps]", url = "http://stardust.wavestreamer.com:2152/1" },
{ name = "Classic FM [128kbps]", url = "http://ng.btv.bg/m3u/classicfm.m3u" },
{ name = "MDR Klassik [128kbps]", url = "http://c22033-l.i.core.cdn.streamfarm.net/22008mdrklassik/live/3087mdrklassik/live_de_128.mp3" },
{ name = "Radio Orfey [128kbps]", url = "mms://live.rfn.ru/orfey-128" },
{ name = "Radio Cultura [128kbps]", url = "mms://live.rfn.ru/rcult" },
{ name = "classicalways [128kbps]", url = "http://listen.radionomy.com/classicalways" },
{ name = "Classical Music Archives [128kbps]", url = "http://radio.classicalarchives.com:8000/" },
{ name = "AirClassique [128kbps]", url = "http://listen.radionomy.com/air-classique" },
{ name = "Ambianceclassique [128kbps]", url = "http://listen.radionomy.com/ambiance-classique" },
{ name = "Radio Swiss Classic [128kbps] ", url = "http://stream.srg-ssr.ch/m/rsc_de/mp3_128" },
{ name = "RadioMozart [128kbps]", url = "http://listen.radionomy.com/radio-mozart" },
{ name = "Venice Classic Radio Italia [128kbps]", url = "http://109.123.116.202:8020" },
{ name = "Staroe Radio Music [128kbps]", url = "http://195.91.237.50:8000/music128" },
{ name = "Radio 4 ashdown [128kbps]", url = "http://radio.north.kz:8000/ashdown" },
{ name = "Baltkom [128kbps]", url = "http://radio.north.kz:8000/baltkom" },
{ name = "Staroe Radio (Detskoe) [128kbps]", url = "http://195.91.237.50:8000/detskoe128" },
{ name = "Makradio Detskiy Hit [128kbps]", url = "http://81.19.85.203/makdeti128.mp3" },
{ name = "Makradio Retro Hit [128kbps]", url = "http://81.19.85.203/mix128.mp3" },
{ name = "Retro FM [128kbps]", url = "http://radio.north.kz:8000/retrofm-128" },
{ name = "Discotheque 80s [128kbps]", url = "http://81.19.85.204/disco128.mp3" },
{ name = "RDD Radio for two [128kbps]", url = "http://81.19.85.203/rdd128.mp3" },
{ name = "Klara Belgium high[128kbps]", url = "http://mp3.streampower.be/klara-high" },
{ name = "Radio Mozart [128kbps]", url = "http://listen.radionomy.com/radio-mozart.m3u" },
{ name = "Poland Classical [128kbps]", url = "http://91.121.92.167:8900" },
{ name = "FIP [128k]", url = "http://mp3.live.tv-radio.com/fip/all/fiphautdebit.mp3" },
{ name = "KUHF_Classical USA [128kbps]", url = "http://129.7.48.200/KUHF_Classical_Hifi" },
{ name = "Rete Toscana Classica Firenze Italia", url = "mms://streaming.intoscana.it/wmtencoder/rtc.wma" },
{ name = "ARS NOVA -Early Music Poland [128kbps]", url = "http://37.59.8.151:8200" },
{ name = "Türkiye ITÜ Radyosu Klasik [128kbps]", url = "http://160.75.86.29:8097/" },
{ name = "Northern Cyprus Bayrak Klasik [128kbps]", url = "http://sc.brtk.net:8006/" },
{ name = "KEXP Seattle [128kbps]", url = "http://live-mp3-128.kexp.org:8000/" },
{ name = "Ukraine  MyRadio Classical music [128kbps]", url = "http://music.myradio.ua:8000/Classica128.ogg" },
{ name = "Bulgaria  Classic FM [128kbps]", url = "http://live.btvradio.bg:8000/classic-fm.mp3" },
{ name = "France  Radio Classique 128k", url = "http://broadcast.infomaniak.net:80/radioclassique-high.mp3" },
{ name = "France Musique [128kbps]", url = "http://www.tv-radio.com/station/france_musique_mp3/france_musique_mp3-128k.m3u" },
{ name = "Jazz  tsfjazz France [128kbps]", url = "http://tsfjazz.ice.infomaniak.ch:80/tsfjazz-high" },
{ name = "Bayern 4 Klassik [128kbps]", url = "http://gffstream.ic.llnwd.net/stream/gffstream_w13a" },
{ name = "SwissRadio Küsnacht, Swiss [128kbps]", url = "http://www.swissradio.ch/streams/6034.asx" },
{ name = "Venice Classic Radio ITALIA [128kbps]", url = "http://www.veniceclassicradio.eu/live1/128.asx" },
{ name = "SwissRadio Küsnacht, Swiss Opera [128kbps]", url = "http://www.swissradio.ch/streams/6060.asx" },
{ name = "RTVE3  Cuando los elefantes sueñan con la música 15H00 [128kbps]", url = "http://195.10.10.226/rtve/radio3.mp3" },
{ name = "Radio Suisse Classique [128kbps]", url = "http://www.radiosuisseclassique.ch/live/mp3.m3u" },
{ name = "Austria RadioStephansdom [128kbps]", url = "http://srvhost24.serverhosting.apa.net:8000/rsdstream128.m3u" },
{ name = "Espana Radio Clasica [128kbps]", url = "http://radioclasica.rtve.stream.flumotion.com/rtve/radioclasica.mp3.m3u" },
{ name = "Deutschland MDR Figaro [128kbps]", url = "http://avw.mdr.de/livestreams/mdr_figaro_live_128.m3u" },
{ name = "Deutschland MDR Klassik [128kbps]", url = "http://avw.mdr.de/livestreams/mdr_klassik_live_128.m3u" },
{ name = "MyRadio.com.ua [128kbps]", url = "http://music.myradio.com.ua:8000/Classica128.ogg" },
{ name = "Czech classic [128kbps]", url = "http://www.play.cz/radio/classic128.asx" },
{ name = "Belgium RTBF Musiq 3 French-Speaking [128kbps]", url = "http://broadcast.infomaniak.net:80/musiq3-128.mp3" },
{ name = "Estonia Klassikaraadio [128kbps]", url = "http://icecast.err.ee:80/klassikaraadio.mp3" },
{ name = "Latvijas Radio 3 Klasika [128kbps]", url = "mms://lr1w.latvijasradio.lv/pplr3" },
{ name = "Radio-Orfei RUSSIA ", url = "mms://live.rfn.ru/orfey-128/" },
{ name = "POLSKASTACJA .PL ))) EDEN (New Age & World Music) (Polskie Radio) [128kbps]", url = "http://91.121.89.153:9900" },
{ name = "ELDORADIO - Chill Channel [128kbps]", url = "http://sc-chill.eldoradio.lu:80/" },
{ name = "Nirvana Radio - Music for Meditation and Relaxation", url = "http://174.142.192.209:9022" },
{ name = "OCEAN WAVES AMBIENT [128kbps]", url = "http://174.142.192.209:9022" },
{ name = "Nirvana Ambient Radio - The Best Ambient Music [128kbps]", url = "http://81.219.54.6:8002" },
{ name = "Chroma Ambient [128kbps]", url = "http://69.70.125.26:100" },
{ name = "Dub Lubin Radio : Zen Mantra - Live Meditation [128kbps]", url = "http://69.70.125.26:100" },
{ name = "Kral FM Istanbul-Turkish Arabesque music [128kbps]", url = "http://shoutcastdogus.cdnturk.com:80/stream/7/" },
{ name = "Classical Persian [http://www.iranianradio.com/#](http://www.iranianradio.com/#) [128kbps]", url = "http://213.73.255.244:10700" },
{ name = "CALMRADIO.COM - PERSIA [128kbps]", url = "http://206.190.129.220:11808" },


{ name = "Finland YLE Ylen Klassinen [192kbps]", url = "mms://mediau.yle.fi/liveklassinen" },
{ name = "Norway Radio Klassisk [192kbps]", url = "http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h" },
{ name = "Denmark  dr.dk 192kbps]", url = "http://live-icy.gss.dr.dk:8000/A/A04H.mp3" },
{ name = "Denmark  Radio Klassisk [192kbps]", url = "http://onair.100fmlive.dk:80/klassisk_live.mp3" },
{ name = "Sverige-Sweden 1 [192kbps]", url = "http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls" },
{ name = "Sverige-Sweden 2 [192kbps]", url = "http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls" },
{ name = "BBC Radio3 [192kbps]", url = "http://bbc.co.uk/radio/listen/live/r3.asx" },
{ name = "P2 musik Sverige-Sweden [192kbps]", url = "http://http-live.sr.se/p2musik-aac-192" },
{ name = "Finland Classic [192kbps]", url = "http://stream.radioclassic.fi:8000/stream/1/" },
{ name = "Radio Sri Chinmoy - spiritual music for meditation [192kbps]", url = "http://96.126.107.232:8000/" },
{ name = "Klasszik Radio 92.1 [192kbps]", url = "http://online.klasszikradio.hu:80/stream/3/" },

{ name = "ProFM Clasic [224kbps]", url = "http://live.btvradio.bg/clasic.mp3.m3u" },

{ name = "Concertzender [256kbps]", url = "http://streams.greenhost.nl:8080/live" },
{ name = "WBAA Purdue University Indiana [256k]", url = "http://audio-new.wbaa.purdue.edu:8000/wbaa-fm" },
{ name = "SRR Radio România Muzical [256kbps]", url = "http://stream2.srr.ro:8022/" },
{ name = "Holland  AVRO Baroque around the clock [256kbps]", url = "http://icecast.omroep.nl/radio4-baroque-bb-mp3" },
{ name = "Holland  AVRO De Klassiek 24/7 [256kbps]", url = "http://icecast.omroep.nl:80/radio4-klassieken-bb-mp3" },
{ name = "Jazz  CRo Jazz Prague Czech Republic [256kbps]", url = "http://stream3.rozhlas.cz:8000/jazz_high.ogg" },
{ name = "Slovak Radio Klasika [256kbps]", url = "http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u" },
{ name = "Slovak Radio Devin [256kbps]", url = "http://live.slovakradio.sk:8000/Devin_256.mp3.m3u" },
{ name = "Finland rondofm [256kbps]", url = "http://stream.iradio.fi:8000/klasu-hi.mp3" },

{ name = "Linn Classical [320kbps]", url = "http://89.16.185.174:8003/stream" },
{ name = "Audiophile Jazz [320kbps]", url = "http://50.7.173.162:2199/tunein/jazz.pls" },
{ name = "Audiophile Baroque [320kbps]", url = "http://50.7.173.162:2199/tunein/baroque.pls" },
{ name = "Audiophile Classical [320kbps]", url = "http://50.7.173.162:2199/tunein/classical.pls" },
{ name = "Audiophile Live [320kbps]", url = "http://50.7.173.162:2199/tunein/live.pls" },

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

----------------------------------------------------------------------------------------------------

---

### Post by shantiq on 2014-04-12
Hi guys   still on 13.10    and wondering is this marvellous lua script still works  fine in 14.04


now in 13.10 we have VLC media player 2.0.8 Twoflower
in 14.10 you have [COLOR=#555555][FONT=Open Sans]VLC 2.1.2 Rincewind
[/FONT][/COLOR]
now does the script still get picked up here


i tried Rincewind on 13.10[COLOR=#555555][FONT=Open Sans]

[/FONT][/COLOR][COLOR=#800000]**then tho no radio applet**[/COLOR];    so my question is any of you got this going successfully in 14.04 with Rincewind?      thANx in advance for input 

 i downgraded again to 2.0.8  and back it is


PS  I am waiting for a month or two into 14.04 since i only have one machine and have had my fingers burnt before :]]] but i want to know if the script is still ok if any of you have got it going successfully   thanx 
[COLOR=#555555][FONT=Open Sans]





[/FONT][/COLOR]

---

### Post by andrew.46 on 2014-04-12
> **shantiq said:**
> Hi guys   still on 13.10    and wondering is this marvellous lua script still works  fine in 14.04

I am still running a guide to build the development version of vlc and this guide has been updated for 14.04 last week. Good news is that the script works very nicely on this and I would assume would also work on the release version.

---

### Post by shantiq on 2014-04-13
Ha thanx Andrew maybe the PPA i used did not do what the standard release of VLC on 14.04 does...   anyway cool this little applet matters to me much
PS added 5 prog rock stations to the list for us all 70s dudes [Purple Piper]("http://www.purplepiper.eu/") is a corker by the way!

---

### Post by shantiq on 2014-08-15
Time for an update as just found a [Czech classical radio station]("http://www.rozhlas.cz/d-dur/portal/") which broadcasts in Flac   ....  we have found the Holy Grail

```
[noparse]http://radio.cesnet.cz:8000/cro-d-dur.flac[/noparse]

```
 updated in [original post]("http://ubuntuforums.org/showthread.php?t=2180170&p=12813875#post12813875")  and also added as pls [ATTACH]255501[/ATTACH]

---

### Post by andrew.46 on 2014-09-15
> **shantiq said:**
> Time for an update as just found a [Czech classical radio station]("http://www.rozhlas.cz/d-dur/portal/") which broadcasts in Flac   ....  we have found the Holy Grail

```
[noparse]http://radio.cesnet.cz:8000/cro-d-dur.flac[/noparse]
```


Great sound, you are the man Shan :)

---

