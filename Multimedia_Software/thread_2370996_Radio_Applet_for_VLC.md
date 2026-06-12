---
title: "Radio Applet for VLC"
date: 2017-09-09
forum: Multimedia Software
---

### Post by shantiq on 2017-09-09
This is something I posted here a few years back but now updated as all changes on the net if you look away for a year :]


All credit to :

 ***Authors: Ben Dowling*** ([http://www.coderholic.com/extending-vlc-with-lua/](http://www.coderholic.com/extending-vlc-with-lua/))  
 Streaming Radio Player extension for VLC
 Radio Stations Picked by Shantiq - Links do not always last as long as one would wish them too :]
 To update use Google - [http://www.listenlive.eu/](http://www.listenlive.eu/) can be of use too and shoutcast.com to add update stations
All stations working as of Sept 2017 - Radio Darvish not on all the time

* &#10122; copy the following text into a text editor*

```

--[[
 Streaming Radio Player extension for VLC
 Authors: Ben Dowling (http://www.coderholic.com)
 Radio Stations Picked by Shantiq - Links do not always last as long as one would wish them too :]
 To update use Google - http://www.listenlive.eu/ can be of use too and shoutcast.com to add update stations
--]]

 
stations = {
    

{ name = "BBC Radio3 HD", url = "http://as-hls-uk-live.akamaized.net/pool_7/live/bbc_radio_three/bbc_radio_three.isml/bbc_radio_three-audio=320000.norewind.m3u8" },
{ name = "Norway Radio Klassisk 192", url = "http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h" },
{ name = "Radio Planeta Occitania", url = "http://www.radioking.com/play/radio-planeta-occitania" },
{ name = "Radio Darvish", url = "http://50.22.218.73/stream.mp3?ipport=50.22.218.73_24445" },
{ name = "HiOnline World Radio [Holland]", url = "http://82.94.205.73/proxy/onlineworldradio?mp=/" },
{ name = "Bayern 4 Klassik", url = "http://br-brklassik-live.cast.addradio.de/br/brklassik/live/mp3/128/stream.mp3" },
{ name = "&#1050;ripalu", url = "http://68.168.101.146:8417" },
{ name = "RKC Radio Krishna Centrale", url = "http://81.25.96.13:8090" },
{ name = "Ambient Sleeping Pill", url = "http://radio.stereoscenic.com/asp-h" },
{ name = "Chroma Radio", url = "http://148.251.184.14:8004" },
{ name = "Venice Classic Radio ITALIA", url = "http://www.veniceclassicradio.eu/live1/128.asx" },
{ name = "PPP Purple piper Progressive", url = "http://s1.shoutitaly.com:8036/" },
{ name = "Radio Suisse Classique", url = "http://www.radiosuisseclassique.ch/live/mp3.m3u" },
{ name = "Austria RadioStephansdom", url = "http://81.223.232.160:8000/live128" },
{ name = "France Musique", url = "http://direct.francemusique.fr/live/francemusique-midfi.mp3" },
{ name = "Espana Radio Clasica", url = "http://radioclasica.rtveradio.cires21.com/radioclasica/mp3/icecast.audio" },
{ name = "Slovak Radio Klasika", url = "http://live.slovakradio.sk:8000/Klasika_256.mp3.m3u" },
{ name = "Slovak Radio Devin", url = "http://live.slovakradio.sk:8000/Devin_256.mp3.m3u" },
{ name = "Sverige-Sweden 1", url = "http://sverigesradio.se/topsy/direkt/1603-hi-mp3.pls" },
{ name = "Sverige-Sweden 2", url = "http://sverigesradio.se/topsy/direkt/2562-hi-mp3.pls" },
{ name = "Czech classic", url = "http://www.play.cz/radio/classic128.asx" },
{ name = "P2 musik Sverige-Sweden", url = "http://http-live.sr.se/p2musik-aac-192" },
{ name = "Ancient FM - www.ancientfm.com", url = "http://simplexstream.com:8058" },
{ name = "&#1050;&#1083;&#1072;&#1089;&#1089;&#1080;&#1095;&#1077;&#1089;&#1082;&#1072;&#1103; &#1084;&#1091;&#1079;&#1099;&#1082;&#1072; MyRadio.com.ua  ", url = "http://music.myradio.com.ua:8000/Classica128.ogg" },

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

[I]&#10123; Save file to /usr/lib/vlc/lua/extensions/VLCRadio.lua
&#10124; Open VLC/View/Streaming Radio Player
&#10125; Enjoi![/I]

[[IMG]https://s26.postimg.org/pui9phuph/image.png[/IMG]]("https://postimg.org/image/pui9phuph/")

---

