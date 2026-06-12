---
title: "[SOLVED] Mythweather 18hr 3 day and 6 day forcast problems"
date: 2008-11-25
forum: Mythbuntu
---

### Post by nrune on 2008-11-25
Well the current conditions, and radar work fine, but I can not get the 18 hour, 3 day, 6 day forcast to work at all.  No idea what is wrong.  here is the mythfrontend log.  
> 
2008-11-25 17:11:28.831 Starting update of NDFD-18_Hour
2008-11-25 17:11:28.852 Starting update of NWS-XML
2008-11-25 17:11:28.948 Starting update of NDFD-6_day
2008-11-25 17:11:29.552 Starting update of Animated-Map-Download
QSocketNotifier: Multiple socket notifiers for same socket 40 and type read
2008-11-25 17:11:32.539 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/nrune/.mythtv/MythWeather/NWS-XML KMFV has exited
2008-11-25 17:11:40.068 nice /usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl -u ENG -d /home/nrune/.mythtv/MythWeather/Animated-Map-Download [http://images.weather.com/looper/archive/us_ec_9regradar_plus_us](http://images.weather.com/looper/archive/us_ec_9regradar_plus_us) has exited
2008-11-25 17:11:54.223 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/nrune/.mythtv/MythWeather/NDFD-18_Hour +37.39,-075.46 has exited
2008-11-25 17:11:55.142 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/nrune/.mythtv/MythWeather/NDFD-6_day +37.39,-075.46 has exited
2008-11-25 17:21:29.688 Starting update of Animated-Map-Download
2008-11-25 17:21:33.465 nice /usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl -u ENG -d /home/nrune/.mythtv/MythWeather/Animated-Map-Download [http://images.weather.com/looper/archive/us_ec_9regradar_plus_us](http://images.weather.com/looper/archive/us_ec_9regradar_plus_us) has exited
2008-11-25 17:26:28.940 Starting update of NDFD-18_Hour
2008-11-25 17:26:28.992 Starting update of NWS-XML
2008-11-25 17:26:29.071 Starting update of NDFD-6_day
2008-11-25 17:26:32.108 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/nrune/.mythtv/MythWeather/NWS-XML KMFV has exited
2008-11-25 17:26:32.611 NVP: prebuffering pause
2008-11-25 17:26:34.483 NVP: Prebuffer wait timed out 10 times.

Any help appreciated. 
Thanks

---

### Post by nrune on 2008-11-25
Further cluelessness. 

Results after running: 
```
nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/nrune/.mythtv/MythWeather/NDFD-6_day +37.39,-075.46

```

commandline output:
```
3dlocation::Melfa / Accomack Airport, VA
6dlocation::Melfa / Accomack Airport, VA
updatetime::Last Updated on Nov 25, 06:54 PM EST
low-0::36
high-0::53
icon-0::pcloudy.png
low-1::42
high-1::55
icon-1::pcloudy.png
low-2::45
high-2::53
icon-2::thunshowers.png
low-3::44
high-3::51
icon-3::pcloudy.png
low-4::41
high-4::51
icon-4::pcloudy.png
low-5::40
high-5::49
icon-5::pcloudy.png
date-0::Wednesday
date-1::Thursday
date-2::Friday
date-3::Saturday
date-4::Sunday
date-5::Monday

```

So the script is scraping the site

and this is the output of ndfd_cache_+37.39_-075.46
> 2008-11-25T17:50:53 2008-11-25T16:56:53
$VAR1 = {'2008-11-25T07:00:00-0500,2008-11-25T19:00:00-0500' => {'probability-of-precipitation_12 hour' => '40'},'2008-11-25T19:00:00-0500' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg','temperature_hourly' => '48'},'2008-11-25T19:00:00-0500,2008-11-26T07:00:00-0500' => {'probability-of-precipitation_12 hour' => '1'},'2008-11-25T22:00:00-0500' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg','temperature_hourly' => '46'},'2008-11-26T01:00:00-0500' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nsct.jpg','temperature_hourly' => '43'},'2008-11-26T04:00:00-0500' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/nfew.jpg','temperature_hourly' => '44'},'2008-11-26T07:00:00-0500' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/few.jpg','temperature_hourly' => '41'},'2008-11-26T07:00:00-0500,2008-11-26T19:00:00-0500' => {'probability-of-precipitation_12 hour' => '0'},'2008-11-26T10:00:00-0500' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/sct.jpg','temperature_hourly' => '45'},'2008-11-26T13:00:00-0500' => {'conditions-icon_forecast-NWS' => 'http://forecast.weather.gov/images/wtf/sct.jpg','temperature_hourly' => '48'}};

So if the script is working why is mythtv not displaying it? 

Thanks

---

### Post by nrune on 2008-11-26
Okay I have uninstalled and then reinstalled, I have changed themes, and I have rolled it back to the previous version, still no go with 18hr, 3 day, and 6 day forcast.  Any ideas? 

Thanks

---

### Post by mrand on 2008-11-26
What version?  8.04.01?  8.04+weeklyfixes?  8.10?  8.10+weeklyfixes?

---

### Post by nrune on 2008-11-26
Running 8.10 current version 0.21.0 fixes 18722 most current in ubuntu repo's.

Thanks

Just upgraded to 18961 and having the same issue.

---

### Post by nrune on 2008-11-29
Well only thing left is a total reinstall.  I have cleaned out the database of all settings, mythweather is running fine on my frontend backend combo machine with all screens showing. I have changed themes and it is just not working. 

Could font size be an issue?  

Any other clue out there? 

Thanks
Nrune

---

### Post by nrune on 2008-11-30
Solved, 
10% reduction in font size under appearance and then mythweather was able to display the info.  issue closed.:lolflag:

---

