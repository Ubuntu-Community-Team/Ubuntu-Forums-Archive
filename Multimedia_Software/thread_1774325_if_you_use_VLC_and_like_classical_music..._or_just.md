---
title: "if you use VLC and like classical music... or just radio"
date: 2011-06-03
forum: Multimedia Software
---

### Post by shantiq on 2011-06-03
save as classical.lua and place in  ~/.local/share/vlc/lua/extensions


```
sudo cp classical.lua  ~/.local/share/vlc/lua/extensions

```    You may need to create the folders lua and extensions if they are not already there.

Lua extension designed by Ben Dowling 

Of course you can use for any radio stations of your choice
Here my list is ClaSsical European and high sound quality...


```

--[[
 Streaming Radio Player extension for VLC &gt;= 1.1.0
 Authors: Ben Dowling (http://www.coderholic.com)
--]]
 
stations = {
	

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

---

### Post by wolfen69 on 2011-06-03
I'm assuming I have to make /lua/extensions folders, as they don't exist for me. Where in VLC, would this extension show up?

---

### Post by shantiq on 2011-06-03
der :KS:KS:KSwolfen i forgot to say did i not?


click on **view** and right on top of allocine lua extension
and then the streamer pops up it has the name Streaming Radio Player

and yes create the lua and extensions folders

---

### Post by andrew.46 on 2011-06-03
Thanks shantiq works very nicely here. Where did you find this one?

---

### Post by mc4man on 2011-06-03
> **andrew.46 said:**
> Thanks shantiq works very nicely here. Where did you find this one?
Maybe here
[http://www.coderholic.com/extending-vlc-with-lua/](http://www.coderholic.com/extending-vlc-with-lua/)

(would be interesting to find 3rd party lua scripts

---

### Post by andrew.46 on 2011-06-03
> **mc4man said:**
> Maybe here
[http://www.coderholic.com/extending-vlc-with-lua/](http://www.coderholic.com/extending-vlc-with-lua/)

As indicated in the lua script I guess..... sometimes I can be really thick :(

---

### Post by mc4man on 2011-06-03
> **andrew.46 said:**
> As indicated in the lua script I guess..... :(
Well it's possible shantiq found it or a ref on another site with some others - 
This one, Streaming Radio Player, will prove to be  quite useful

---

### Post by shantiq on 2011-06-04
:)well guys from**[B][ here]("http://www.coderholic.com/extending-vlc-with-lua/")**[/B] and yes it was [**Ron999**]("http://ubuntuforums.org/member.php?u=139331") from this forum who showed me it for which i am enormously grateful :wink::-)
I thought many of you would like it too



ps    this is a [**good site**]("http://www.listenlive.eu/index.html") to find radio stations to add to your list


one other huge place to find radio is**[ here ]("http://comfm.com/")**


If any of you know of similar lists of stations feel free to add here 
 :KS

---

### Post by coffeecat on 2011-06-04
@shantiq, many thanks for posting this.

> **shantiq said:**
> 
If any of you know of similar lists of stations feel free to add here 
 

Another one for your list. Classic FM in the UK.

[http://www.classicfm.co.uk/](http://www.classicfm.co.uk/)

I found the streaming URL on its FAQ page. Since it lists Ubuntu by name I think we ought to add it. :)

[http://www.classicfm.co.uk/on-air/ways-of-listening/listen-faqs/#jump-linux](http://www.classicfm.co.uk/on-air/ways-of-listening/listen-faqs/#jump-linux)

This is the line I added to classical.lua:

```
{ name = "Classic FM", url = "http://mediaweb.musicradio.com/Show.asx?StreamID=2" },
```

---

### Post by shantiq on 2011-06-04
Thanx coffeecat    great programming that station too sadly it has ads :KS:KS  but cool thanx will add it here
on the list

I aimed to have a list with over 128kbps stations the Norway one NRK is 384 and the BBC radio3 HD is 320 which gives a great sound

One day ( soon ) we shall have lossless radio :KS

---

### Post by 1956moonraker on 2011-10-28
> **shantiq said:**
> save as classical.lua and place in  ~/.local/share/vlc/lua/extensions


```
sudo cp  ~/.local/share/vlc/lua/extensions

```    You may need to create the folders lua and extensions if they are not already there.

Lua extension designed by Ben Dowling 

Of course you can use for any radio stations of your choice
Here my list is ClaSsical European and high sound quality...


```
--[[
 Streaming Radio Player extension for VLC &gt;= 1.1.0
 Authors: Ben Dowling (http://www.coderholic.com)
--]]
 
stations = {
	

{ name = "BBC Radio3 HD", url = "http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls" },
{ name = "Norway Radio Klassisk HD", url = "http://lyd.nrk.no/nrk_radio_klassisk_wma_h" },
{ name = "Radio Mozart", url = "http://listen.radionomy.com/radio-mozart.m3u" },
{ name = "Poland", url = "http://91.121.92.167:8900" },
{ name = "Classic FM", url = "http://mediaweb.musicradio.com/Show.asx?StreamID=2" },
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

Many thanks, Shantiq, works perfectly. In Ubuntu the location for the .lua file is /usr/lib/vlc/extensions already made by vlc on installation.
Cheers

---

### Post by shantiq on 2011-10-28
```
/usr/lib/vlc/extensions already made by vlc on installation
```

well moonraker not on mine it is not
but there is 

```
/usr/lib/vlc/lua/extensions
```  so maybe from now will put it there   actually no i won't just tried it and it does not get picked up not sure why...

---

### Post by andrew.46 on 2012-12-25
Hmmm.... can anybody get this working for vlc 2.0.5? Not working here after working beautifully on older versions :(

---

### Post by mc4man on 2012-12-25
> **andrew.46 said:**
> Hmmm.... can anybody get this working for vlc 2.0.5? Not working here after working beautifully on older versions :(
As in 'not showing up' or 'showing up but not working'?

Works ok here,(atm repo 13.04 vlc), have used the ext.  to add more stations

---

### Post by overdrank on 2012-12-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

