---
title: "Getting a root shell from Huawei E303"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by sgoodman on 2012-08-01
i am trying to get more from my Huawei E303. This is what i investigated so far:

the locations of various functions. right now i am investigating the api section.

```
js

http://192.168.1.1/js/changelang.js
http://192.168.1.1/js/main.js
http://192.168.1.1/js/redirect.js
http://192.168.1.1/js/traffic.js
http://192.168.1.1/js/index.js


lib

http://192.168.1.1/lib/jquery-1.4.4.js
http://192.168.1.1/lib/log4javascript_lite.js
http://192.168.1.1/lib/jquery.qtip.js


api

http://192.168.1.1/api/redirection/homepage
http://192.168.1.1/api/monitoring/traffic-statistics
http://192.168.1.1/api/sms/sms-list
http://192.168.1.1/api/monitoring/status


http://192.168.1.1/api/net/current-plmn

    0: hilink_label_2g,
    2: hilink_label_3g


Public land mobile network

index.js uses function for current-plmn


http://192.168.1.1/api/language/current-language
http://192.168.1.1/api/monitoring/check-notifications
http://192.168.1.1/api/user/logout
http://192.168.1.1/api/global/module-switch
http://192.168.1.1/api/dialup/dial


api/monitoring/clear-traffic

http://192.168.1.1/api/monitoring/converged-status = api/pin/status + api/pin/simlock + api/language/current-language



usermanual

http://192.168.1.1/usermanual/en-us/usermanual/web_content_concept_1.html

config

http://192.168.1.1/config/help/helplanglist.xml
http://192.168.1.1/config/global/languagelist.xml

language

http://192.168.1.1/language/lang_en_us.js
http://192.168.1.1/language/lang_de_de.js

css

http://192.168.1.1/css/main.css
http://192.168.1.1/css/main_Arabic.css

html
http://192.168.1.1/html/leftmenu.html
http://192.168.1.1/html/traffic.html
http://192.168.1.1/html/index.html
http://192.168.1.1/html/footer.html

res

http://192.168.1.1/res/dialog_close_btn.gif

```next step: i will create a shell script that outputs the status of the connection and the amount of data transferred.

the overall goal is get root shell access. there is a way for sure. wether via the wwwserver or dma access.

---

### Post by BlackyPanther on 2012-09-06
Hey,
tried some features of the stick...
here my notices:
```

all responses as XML => BashParsing via sed -e

Status: http://hi.link/api/monitoring/status (GET)
    ConnectionStatus:
        112 = no autoconnect
        113 = no autoconnect on roaming
        114 = no reconnect
        115 = no reconnect on roaming
        900 = connecting
        901 = connected
        902 = disconnected
        903 = disconnecting
    
                   |    discon      |      con      |
                   |   2G   |   3G  |   2G  |   3G  |
      NetworkType: |   3    |   4   |   3   |  4/7  |
      3 = 2G / 4 = 3G (UMTS) / 7 = 3G+ (HSDPA)

    SignalStrength: strength in percent
    
    ServiceStatus: 1 = enter PIN / 2 = PIN correkt
    SimStatus: 0 = no SIM access / 1 = SIM access


Provider: http://hi.link/api/net/current-plmn (GET)

Dis/Connecting: http://hi.link/api/dialup/dial (POST)
    connect:
        <?xml version="1.0" encoding="UTF-8"?><request><Action>1</Action></request>
    disconnect:
        <?xml version="1.0" encoding="UTF-8"?><request><Action>0</Action></request>

Messages: http://hi.link/api/monitoring/check-notifications (GET)

Statistics and Traffic: http://hi.link/api/monitoring/traffic-statistics (GET)

// Tbc

```

---

### Post by sgoodman on 2012-09-07
i made a script for getting some info from my stick.

[[img]http://www.freeimagehosting.net/t/2mksp.jpg[/img]](http://www.freeimagehosting.net/2mksp)

code follows

```

#!/bin/bash

daten_holen(){
    Provider=($(wget http://192.168.1.1/api/net/current-plmn -O - -o /dev/null | xml2 | egrep '/response/FullName=|/response/Numeric=|/response/Rat=' | cut -d "=" -f 2))

    Verbindung=($(wget http://192.168.1.1/api/monitoring/status -O - -o /dev/null | xml2 | egrep '/response/ConnectionStatus=|/response/SignalIcon=|/response/RoamingStatus=0|/response/WanIPAddress=' | cut -d "=" -f 2))

    Verbrauch=($(wget http://192.168.1.1/api/monitoring/traffic-statistics -O - -o /dev/null | xml2 | cut -d "=" -f 2))
}

extip(){
    real_ip=($(wget http://www.geoiptool.com/ -O - -o /dev/null | grep 'align="left" class="arial_bold">' | cut -d ">" -f 2 | cut -d "<" -f 1 | sed '/^$/d'))
}

verb_status(){
 # Verbinde = 900 Trenne 903 Verbunden 901 Getrennt 902
    case $1 in
        900)
            echo Verbinde
            ;;
        901)
            echo Verbunden
            ;;
        902)
            echo Getrennt
            ;;
        903)
            echo Trenne
            ;;
        *)
            echo Fehler
    esac
}

netz_standard(){
 # Verbinde = 900 Trenne 903 Verbunden 901 Getrennt 902
    case $1 in
        0)
            echo 2G
            ;;
        2)
            echo 3G
            ;;
        *)
            echo unbekannt
    esac
}

roaming(){
    case $1 in
        0)
            echo nein
            ;;
        1)
            echo aktiv
            ;;
        *)
            echo unbekannt
    esac
}

getCurrentTime(){
    hours=$(($1 / 3600))
    if test $hours -gt 9
    then
        ergebnis=$hours':'
    elif test $hours -gt 0
    then
        ergebnis='0'$hours':'
    elif test $hours -eq 0
    then
        ergebnis='00:'
    fi
    sek=$(($1 - $hours * 3600))

    minuten=$(($sek / 60))
    if test $minuten -gt 9
    then
        ergebnis=$ergebnis$minuten':'
    elif test $minuten -gt 0
    then
        ergebnis=$ergebnis'0'$minuten':'
    elif test $minuten -eq 0
    then
        ergebnis=$ergebnis'00:'
    fi
    sek=$(($sek - $minuten * 60))

    if test $sek -gt 9
    then
        ergebnis=$ergebnis$sek
    elif test $sek -gt 0
    then
        ergebnis=$ergebnis'0'$sek
    elif test $sek -eq 0
    then
        ergebnis=$ergebnis'00'
    fi    
    
    echo -n $ergebnis
}

getTraffic(){
    g_monitoring_dumeter_kb=1024
    g_monitoring_dumeter_mb=1048576
    g_monitoring_dumeter_gb=1073741824

    if test $g_monitoring_dumeter_kb -gt $1
    then
        menge=$(echo 'scale=2;' $1 / 1024 | bc -l) 
        menge=$menge' KB'
    elif test $g_monitoring_dumeter_kb -le $1 &&  test $g_monitoring_dumeter_mb -gt $1
    then
        menge=$(echo 'scale=2;' $1 / 1024 | bc -l)
        menge=$menge' KB'
    elif test $g_monitoring_dumeter_mb -le $1 && test $g_monitoring_dumeter_gb -gt $1
    then
        menge=$(echo 'scale=2;' $1 / 1024 / 1024 | bc -l)
        menge=$menge' MB'
    else
        menge=$(echo 'scale=2;' $1 / 1024 / 1024 / 1024 | bc -l )
        menge=$menge' GB'
    fi
    echo -n $menge
}


t=2

while :
do
    clear
    echo -n $(date +%A" "%T)
    daten_holen

    echo -n ' | Netz:' ${Provider[0]}
    echo ' | MCC / MNC Tupel:' ${Provider[1]}
    echo -----------------------------------------------------------
    
    echo -n 'Verbindungsstatus: ' 
    verb_status ${Verbindung[0]}    
    echo -n 'Technik: '
    netz_standard ${Provider[2]}
    echo 'Signalstärke:' ${Verbindung[1]} von 5
    echo -n 'Roaming: '
    roaming ${Verbindung[2]}
    echo

    echo 'IPv4 Adresse:' ${Verbindung[3]}
    echo 'ext. IPv4 Adresse:'
    echo 

    echo -n 'Empfangen: '
    getTraffic ${Verbrauch[3]}
    echo
    echo -n 'Senden:    '
    getTraffic ${Verbrauch[4]}
    echo
    echo

    echo 'Statistik | Diese Sitzung: | Gesamt:'
    echo -n 'Dauer:    | ' 
    getCurrentTime ${Verbrauch[0]} 
    echo -n '         '
    getCurrentTime ${Verbrauch[7]}
    echo

    echo -n 'Versand:  |  ' 
    getTraffic ${Verbrauch[1]}
    echo -n '          '
    getTraffic ${Verbrauch[5]}
    echo

    echo -n 'Empfang:  |  '
    getTraffic ${Verbrauch[2]}
    echo -n '          '
    getTraffic ${Verbrauch[6]}
    echo

    echo
    echo 'warte' $t 'Sekunden' 
    sleep $t
done


```

---

### Post by piccobello on 2012-09-24
Just to make sure, is this device still working in 12.04, and how did you make it work? I'm using Kubuntu. Thanks a lot!

---

### Post by sgoodman on 2012-09-26
> **piccobello said:**
> Just to make sure, is this device still working in 12.04, and how did you make it work? I'm using Kubuntu. Thanks a lot!


Yes i am using my E303 with Linux Mint 13 (maya).

i suspect you get errors like /dev/sr1 could not be mounted ?

---

### Post by piccobello on 2013-02-12
> **sgoodman said:**
> Yes i am using my E303 with Linux Mint 13 (maya).

i suspect you get errors like /dev/sr1 could not be mounted ?

THanks, I was just enquiring before buying.
I can now answer myself: it works out of the box with NetworkManager plasmoid (KDE 12.04) in Italy (provider: Wind). It works also in Belgium (provider: Base), but there I have to use sakis3g, still have to figure out why. Thanks ):P

---

