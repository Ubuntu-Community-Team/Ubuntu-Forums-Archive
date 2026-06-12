---
title: "[SOLVED] hack for NWS-XML weather &quot;Current Conditions&quot; blank on Jaunty"
date: 2009-07-07
forum: Mythbuntu
---

### Post by andrewc6l on 2009-07-07
I've been using NWS-XML to get weather information on MythWeather. A few weeks ago the "Current Conditions" screen stopped working - possibly because NWS stopped reporting windchill? It just showed up as blank.

At any rate, I've hacked /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl and now it works for me. If you are also having trouble with MythWeather current conditions, and are using the NWS-XML script to get the weather, give it a shot.

(Rename it from nwsxml.pl.txt to nwsxml.pl, and remember to save a copy of your original!)

I just checked: this works for SI units, but not for Imperial units. Maybe someone who knows Perl can fix it if you want Farenheit. (Looks like wind gust isn't being detected in Imperial?)

---

### Post by bcg30506 on 2009-07-07
This did not fix my issue.  My current conditions are still a blank screen and I see this in mythfrontend.log:

2009-07-07 22:45:48.666 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2009-07-07 22:45:48.959 SourceManager Error: Can not connect nonexistent source 1

---

### Post by dannyboy79 on 2009-07-08
i ahve a problem with mythweather as well. I have 6 hour forcast and week forcast (i think that's what it's called), also animated map and sever alerts. The only 2 that work are the animated map and th sever alerts. the other 2 are blank. Can you help please? I am using General Mitchel International Airport in Milwaukee, WI as teh source.

---

### Post by andrewc6l on 2009-07-11
It appears that there are several problems with MythWeather. The way to tell if you have the problem I do is to run:

 /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/*mythuser*/.mythtv/MythWeather/NWS-XML KPHX 

If you get values that aren't filled in for windchill (or perhaps windgust / windspgst) then you might have the same problem. If not, it's probably another issue.

I hacked nwsxml.pl some more... now it works for me with both imperial and SI units. (I fill in windgust and windspgst with "NA" because it looks as if NWS isn't reporting them for location KPHX.)

Rename the attached file nwsxml.pl (from nwsxml.pl.2.txt) and be sure to save a copy of the old one. Hope this helps someone!

---

### Post by dannyboy79 on 2009-07-17
> **andrewc6l said:**
> It appears that there are several problems with MythWeather. The way to tell if you have the problem I do is to run:

 /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/*mythuser*/.mythtv/MythWeather/NWS-XML KPHX 

If you get values that aren't filled in for windchill (or perhaps windgust / windspgst) then you might have the same problem. If not, it's probably another issue.

I hacked nwsxml.pl some more... now it works for me with both imperial and SI units. (I fill in windgust and windspgst with "NA" because it looks as if NWS isn't reporting them for location KPHX.)

Rename the attached file nwsxml.pl (from nwsxml.pl.2.txt) and be sure to save a copy of the old one. Hope this helps someone!
 i am using the blue theme and the 6 hour forcast numbers ar overlapping the Temp an Precip words. and the degree symbol is getting cut off. ANy suggestions?

---

### Post by axelsvag on 2009-07-21
I get this error message when I try to use the hack

```
xxx@xxx-mythtv:~$ sudo /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl
Invalid usage at /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl line 72.

```

---

### Post by newlinux on 2009-07-21
> **dannyboy79 said:**
> i am using the blue theme and the 6 hour forcast numbers ar overlapping the Temp an Precip words. and the degree symbol is getting cut off. ANy suggestions?

changing the fonts in weather-ui.xml fixed this problem for me.

---

### Post by newlinux on 2009-07-21
the script didn't work for me - but it got me on the right track - I basically had to set some other values to 'NA' to get it to work properly commandline. Will test in UI later on when I get home.

---

### Post by dannyboy79 on 2009-07-22
> **newlinux said:**
> changing the fonts in weather-ui.xml fixed this problem for me.

and what font did you change it to?

---

### Post by newlinux on 2009-07-22
> **dannyboy79 said:**
> and what font did you change it to?

see my post in your other thread... You can look through that file and see which fonts are used for which displays in case you are having problems with other weather pages.

I'm glad to report current conditions is working again for me.

---

### Post by rsay on 2009-08-08
The file that you posted reduces the number of errors, but doesn't resolve my issue.

Here is the output when I run the script:

```
Warning: XML::LibXML compiled against libxml2 20632, but runtime libxml2 is older 20630
cclocation::Pitt-Greenville Airport, NC
station_id::KPGV
latitude::35.63
longitude::-77.4
observation_time::Last Updated on Aug 8 2009, 8:00 pm EDT
observation_time_rfc822::Sat,  8 Aug 2009 20:00:00 -0400
weather::Fair
temperature_string::82.0 F (28.0 C)
temp::82.0
relative_humidity::58
wind_string::South at 10.4 MPH (9 KT)
wind_dir::South
wind_degrees::190
wind_speed::10.4
wind_gust::NA
Use of uninitialized value in concatenation (.) or string at /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl line 160.
pressure_string::
pressure::30.18
dewpoint_string::66.2 F (19.0 C)
dewpoint::66.2
heat_index_string::84 F (29 C)
heat_index::84
visibility::10.00
weather_icon::fair.png
appt::84
wind_spdgst::10.4 (NA) mph

```

Can you suggest any additional changes that I might be able to make to get things working again?

---

### Post by bcg30506 on 2009-08-17
> **andrewc6l said:**
> It appears that there are several problems with MythWeather. The way to tell if you have the problem I do is to run:

 /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/*mythuser*/.mythtv/MythWeather/NWS-XML KPHX 

If you get values that aren't filled in for windchill (or perhaps windgust / windspgst) then you might have the same problem. If not, it's probably another issue.

I hacked nwsxml.pl some more... now it works for me with both imperial and SI units. (I fill in windgust and windspgst with "NA" because it looks as if NWS isn't reporting them for location KPHX.)

Rename the attached file nwsxml.pl (from nwsxml.pl.2.txt) and be sure to save a copy of the old one. Hope this helps someone!

I am using this new script and now do not get errors in the mythfrontend.log that I used to get with wind chill, but my current conditions screen is still blank.  This is what shows in the log now:

2009-08-17 14:47:09.235 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2009-08-17 14:47:09.533 appt
2009-08-17 14:47:09.533 visibility
2009-08-17 14:47:09.533 weather_icon
2009-08-17 14:47:09.533 wind_spdgst
2009-08-17 14:47:17.019 Starting update of NWS-XML
2009-08-17 14:47:17.043 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/me/.mythtv/MythWeather/NWS-XML KGVL has exited
2009-08-17 14:47:17.043 appt
2009-08-17 14:47:17.043 visibility
2009-08-17 14:47:17.043 weather_icon
2009-08-17 14:47:17.043 wind_spdgst
2009-08-17 14:47:17.234 Starting update of Map-Download
2009-08-17 14:47:17.589 Starting update of Map-Download
2009-08-17 14:47:17.748 nice /usr/share/mythtv/mythweather/scripts/us_nws/maps.pl -u ENG -d /home/me/.mythtv/MythWeather/Map-Download [http://image.weather.com/web/radar/us_se_9regradar_plus_usen.jpg](http://image.weather.com/web/radar/us_se_9regradar_plus_usen.jpg) has exited
2009-08-17 14:47:18.226 nice /usr/share/mythtv/mythweather/scripts/us_nws/maps.pl -u ENG -d /home/me/.mythtv/MythWeather/Map-Download [http://image.weather.com/images/maps/current/cur_se_720x486.jpg](http://image.weather.com/images/maps/current/cur_se_720x486.jpg) has exited

Also, I do not know if it is related or not, but the weather in mythweb doesn't show anything - only a blank page below the mythweb menu icons.  Anyone else have this working?

---

### Post by newlinux on 2009-08-17
> **newlinux said:**
> the script didn't work for me - but it got me on the right track - I basically had to set some other values to 'NA' to get it to work properly commandline. Will test in UI later on when I get home.

> **rsay said:**
> The file that you posted reduces the number of errors, but doesn't resolve my issue.

...
Can you suggest any additional changes that I might be able to make to get things working again?

> **bcg30506 said:**
> I am using this new script and now do not get errors in the mythfrontend.log that I used to get with wind chill, but my current conditions screen is still blank.  This is what shows in the log now:
...



I ended up having to do the same thing for other fields in this file to get it to work... I don't remember which ones, but attached is my file.


> 
Also, I do not know if it is related or not, but the weather in mythweb doesn't show anything - only a blank page below the mythweb menu icons.  Anyone else have this working?

see:

[http://www.mythtvtalk.com/forum/general/11075-mythweb-weather-page-fix.html](http://www.mythtvtalk.com/forum/general/11075-mythweb-weather-page-fix.html)

worked for me...

---

### Post by bcg30506 on 2009-08-17
newlinux, thanks a ton!

Your ideas for mythweb's weather page did work beautifully and it now comes up, though it had current conditions and 6-day forecast blank.

Then I copied your script over mine for the mythweather current conditions fix.  It did not fix my current conditions screen on my TV nor mythweb.  However, it did fill in the 6-day forecast in mythweb when I refreshed the page.

I restarted my mythfrontend and went to Weather and here is the log:

2009-08-17 18:44:42.272 SourceManager: NeedSourceFor: Unable to find source for 5, KGVL, 1
QIntDict: Cannot insert null item
2009-08-17 18:44:42.280 Starting update of NDFD-18_Hour
2009-08-17 18:44:42.284 Starting update of BBC-3day-XML
2009-08-17 18:44:42.293 Starting update of NDFD-6_day
2009-08-17 18:44:42.330 Starting update of Map-Download
2009-08-17 18:44:42.334 Starting update of Map-Download
2009-08-17 18:44:42.361 Starting update of Animated-Map-Download
2009-08-17 18:44:42.372 Starting update of Animated-Map-Download
2009-08-17 18:44:42.384 Starting update of NWS-Alerts
2009-08-17 18:44:42.442 No theme dir: /home/me/.mythtv/themes/Mythbuntu-7.10
2009-08-17 18:44:42.446 MythThemedMenuPrivate: Unknown tag image in background
2009-08-17 18:44:44.473 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbcthreedayxml.pl -u ENG -d /home/me/.mythtv/MythWeather/BBC-3day-XML W0261 has exited
2009-08-17 18:44:44.473 nice /usr/share/mythtv/mythweather/scripts/us_nws/maps.pl -u ENG -d /home/me/.mythtv/MythWeather/Map-Download [http://image.weather.com/images/maps/current/cur_se_720x486.jpg](http://image.weather.com/images/maps/current/cur_se_720x486.jpg) has exited
2009-08-17 18:44:44.473 nice /usr/share/mythtv/mythweather/scripts/us_nws/nws-alert.pl -u ENG -d /home/me/.mythtv/MythWeather/NWS-Alerts 13139 has exited
2009-08-17 18:44:44.724 nice /usr/share/mythtv/mythweather/scripts/us_nws/maps.pl -u ENG -d /home/me/.mythtv/MythWeather/Map-Download [http://image.weather.com/web/radar/us_se_9regradar_plus_usen.jpg](http://image.weather.com/web/radar/us_se_9regradar_plus_usen.jpg) has exited
2009-08-17 18:44:44.844 nice /usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl -u ENG -d /home/me/.mythtv/MythWeather/Animated-Map-Download [http://images.weather.com/looper/archive/southeast_sat_720x486/](http://images.weather.com/looper/archive/southeast_sat_720x486/) has exited
2009-08-17 18:44:44.959 nice /usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl -u ENG -d /home/me/.mythtv/MythWeather/Animated-Map-Download [http://images.weather.com/looper/archive/us_se_4regradar_plus_us](http://images.weather.com/looper/archive/us_se_4regradar_plus_us) has exited
2009-08-17 18:44:45.765 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/me/.mythtv/MythWeather/NDFD-18_Hour +34.16,-083.49 has exited
2009-08-17 18:44:48.892 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2009-08-17 18:44:49.195 SourceManager Error: Can not connect nonexistent source 1
2009-08-17 18:45:05.078 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/me/.mythtv/MythWeather/NDFD-6_day +34.16,-083.49 has exited

---

### Post by newlinux on 2009-08-18
don't know what to say, that file works for me - there may be more fields coming over blank for you that need to be set NA. I just keep setting fields to NA until the file worked for me. It may even be location dependent (maybe there isn't data for some fields in some locations).

---

### Post by bcg30506 on 2009-08-18
I got most of it working now.  The only field that says NA is the Feels Like.  But now current conditions show on both the frontend and mythweb.  I'm using your latest script but had to change my location.  Evidently, the location I previously used is no longer in the source.

Anyone know of where to find a list of all locations online so I can find one closer without the tedious trial-and-error using my remote?

---

### Post by jbfunk05 on 2009-09-28
> **newlinux said:**
> don't know what to say, that file works for me - there may be more fields coming over blank for you that need to be set NA. I just keep setting fields to NA until the file worked for me. It may even be location dependent (maybe there isn't data for some fields in some locations).

I had this same issue but solved it slightly differently: rather than hard coding in fields that should be set to NA I just have the script do a quick check to see if the $xml->{$key} exists before it outputs the data - if it doesn't, it's set to NA.  This way if heat index is empty in the winter and wind chill is empty in the summer you don't have to edit the script seasonally (or just leave out BOTH pieces of data).  I changed this at the end of the nwsxml.pl script:
```

    } else {
        $key = $label;
    }
    printf $label . "::" . $xml->{$key}. "\n";
}
```
to this:
```
    } else {
        $key = $label;
    }
    if ( ! $xml->{$key} ) {
        $xml->{$key} = "NA";
    }
    printf $label . "::" . $xml->{$key}. "\n";
}
```

It worked for me :P

---

