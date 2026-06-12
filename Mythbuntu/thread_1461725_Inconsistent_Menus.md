---
title: "Inconsistent Menus"
date: 2010-04-24
forum: Mythbuntu
---

### Post by uncle hammy on 2010-04-24
I just upgraded all of my systems to 10.04 RC with frsh installations.  I have a be/fe and 2 fe's.  

A little background.  I have buttons to launch Boxee and Hulu in my "Media Library" section, and I also changed the main menu to have "Watch TV" the first option.  Due to this, I copied /usr/share/mythtv/themes/defaultmenu/library.xml and mainmenu.xml to ~/.mythtv on all 3 of my machines so prevent updates from destroying my customizations.  About a two weeks ago (when I was still on 9.10, but upraded to 0.23), on my backend *only* I started getting 2 errors when I tried to browse to Information Center and Settings...."util_menu.xml can't be found" and "info_menu.xml can't be found".  To resolve this (though I found it odd), I copied both those files into ~/.mythtv from /usr/share/mythtv/themes/defaultmenu and all was well in the world.

Well, now I have done fresh 10.04 installs on all my machines, and I have found the source of my issues (I think), though the "why" is rather unexplainable to me.  

On my fe's the default menus (i.e. straight from /usr/share/mythtv/themes/defaultmenu, before I made any changes) go something like....

Media Library
---Watch Recordings
---Watch Videos
---Browse Internet Videos
---Web
Manage Recordings
Information Center
---Weather
---Movies
---System Status
Setup
---General
---Appearance
Watch TV

However, on the be machine, the default menus (i.e. straight from /usr/share/mythtv/themes/defaultmenu, before I made any changes) go something like....

Watch Recordings
Watch Videos
Watch a DVD
Watch TV
Browse Internet Videos
Plugins
---Weather
---Movies
---Web
Advanced
---System Status
---Setup

You get the idea, not even *close* to each other.

When I put my customizations in place on the fe machines, I'm fine.  When I put my customizations in place on the be machine, because of the radically different menu structure, I get those errors again.

So, what gives?  Why would 3 installs off of the same flash drive, all today, all updated to current with auto builds, have such a radically different menu setup?  The only difference in the installs is the addition of the backend on the one machine.  

I did install algae theme on this machine, and I htought it may have something to do with the "custom" menus mentioned here [http://ubuntuforums.org/showthread.php?t=1412645&highlight=algae](http://ubuntuforums.org/showthread.php?t=1412645&highlight=algae) however, I have never downloaded nor installed the custom menus deb.  Also, I have installed algae on the fe machines as well.

---

### Post by uncle hammy on 2010-04-24
OK, now to *really* confuse me, when I open /usr/share/mythtv/themese/defaultmenu/mainmenu.xml on my be machine, the xml is 100% normal.  So where on God's green earth is it getting this other menu layout from?
```

<?xml version="1.0" encoding="UTF-8" ?>
<mythmenu name="MAIN">

    <button>
        <type>MENU_MEDIA_LIBRARY</type>
        <text>Media Library</text>
        <text lang="IT">Multimedia</text>
        <text lang="DE">Mediathek</text>
        <text lang="IS">Margmiðlunarsafn</text>
        <text lang="NL">Mediatheek</text>    
        <text lang="SV">Mediabibliotek</text>
        <text lang="JA">&#12513;&#12487;&#12451;&#12450;&#12521;&#12452;&#12502;&#12521;&#12522;</text>
        <text lang="FI">Mediakirjasto</text>
        <text lang="ZH_TW">&#23186;&#39636;&#39208;</text>
        <text lang="SL">Media</text>
        <text lang="ET">Meediakataloog</text>
        <text lang="ES">Mediateca</text>
        <text lang="PT">Galeria Multimédia</text>
        <text lang="RU">&#1052;&#1091;&#1083;&#1100;&#1090;&#1080;&#1084;&#1077;&#1076;&#1080;&#1072;</text>
        <text lang="AR">&#1605;&#1603;&#1578;&#1576;&#1577; &#1575;&#1604;&#1608;&#1587;&#1575;&#1574;&#1591;</text>
        <text lang="PL">Biblioteka media***</text>
        <text lang="HE">&#1505;&#1508;&#1512;&#1497;&#1514; &#1492;&#1502;&#1491;&#1497;&#1492;</text>
        <text lang="HU">Média könyvtár</text>
        <alttext lang="SV">Bibliotek</alttext>
        <alttext lang="ET">Kataloog</alttext>
        <alttext lang="PT">Galeria</alttext>
        <alttext lang="PL">Galeria</alttext>
        <alttext lang="AR">&#1575;&#1604;&#1605;&#1603;&#1578;&#1576;&#1577;</alttext>
        <action>MENU library.xml</action>
        <description>Play any of your media</description>
        <description lang="DE">Musik hören, Videos ansehen usw.</description>
    </button>
  
    <button>
        <type>MENU_MANAGE_RECORDINGS</type>
        <text>Manage Recordings</text>
        <text lang="IT">Programma Registrazioni</text>
        <text lang="ES">Programar Grabaciones</text>
        <text lang="NL">Opnames Beheren</text>
        <text lang="DE">Aufnahmen verwalten</text>
        <text lang="IS">Upptaka útsendinga</text>
        <text lang="PT">Gerir Gravações</text>
        <text lang="SV">Hantera inspelningar</text>
        <text lang="JA">&#37682;&#30011;&#20104;&#32004;</text>
        <text lang="FI">Hallitse Tallennuksia</text>
        <text lang="ZH_TW">&#31649;&#29702;&#38651;&#35222;&#37636;&#24433;</text>
        <text lang="SL">Posnetki</text>
        <text lang="ET">Salvestamine</text>
        <text lang="RU">&#1059;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1079;&#1072;&#1087;&#1080;&#1089;&#1103;&#1084;&#1080;</text>
        <text lang="AR">&#1571;&#1583;&#1585; &#1575;&#1604;&#1578;&#1587;&#1580;&#1610;&#1604;&#1575;&#1578;</text>
        <text lang="PL">Zarz&#261;dzaj nagraniami</text>
        <text lang="HE">&#1504;&#1497;&#1492;&#1493;&#1500; &#1492;&#1511;&#1500;&#1496;&#1493;&#1514;</text>
        <text lang="HU">Felvételek kezelése</text>
        <alttext lang="DE">Verwaltung</alttext>
        <alttext lang="SV">Hantera</alttext>
        <alttext lang="ES">Programar</alttext>
        <alttext lang="PT">Programação</alttext>
        <alttext lang="RU">&#1047;&#1072;&#1087;&#1080;&#1089;&#1080;</alttext>
        <alttext lang="AR">&#1575;&#1604;&#1578;&#1587;&#1580;&#1610;&#1604;&#1575;&#1578;</alttext>
        <description>Pick and prioritize recordings</description>
        <description lang="DE">Planen Sie Ihre Aufnahmen</description>
        <action>MENU manage_recordings.xml</action>
    </button>

    <button>
        <type>MENU_INFO_CENTER</type>
        <text>Information Center</text>
        <text lang="IT">Centro Informazioni</text>
        <text lang="DE">Informationen</text>
        <text lang="IS">Upplýsinga miðstöð</text>
        <text lang="NL">Informatie Centrale</text>
        <text lang="SV">Informationscenter</text>
        <text lang="JA">&#12452;&#12531;&#12501;&#12457;&#12513;&#12540;&#12471;&#12519;&#12531;&#12475;&#12531;&#12479;&#12540;</text>
        <text lang="FI">Tiedotepalvelu</text>
        <text lang="ZH_TW">&#36039;&#35338;&#20013;&#24515;</text>
        <text lang="SL">Info center</text>
        <text lang="ET">Infokeskus</text>
        <text lang="ES">Centro de Información</text>
        <text lang="EN_GB">Information Centre</text>
        <text lang="PT">Centro de Informação</text>
        <text lang="PL">Centrum informacyjne</text>
        <text lang="RU">&#1062;&#1077;&#1085;&#1090;&#1088; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080;</text>
        <text lang="AR">&#1605;&#1585;&#1603;&#1586; &#1575;&#1604;&#1605;&#1593;&#1604;&#1608;&#1605;&#1575;&#1578;</text>
        <text lang="HE">&#1502;&#1512;&#1499;&#1494; &#1502;&#1497;&#1491;&#1506;</text>
        <text lang="HU">Információk</text>
        <alttext lang="ES">Información</alttext>
        <alttext lang="DE">Infocenter</alttext>
        <alttext lang="SV">Infocenter</alttext>
        <alttext lang="ET">Info</alttext>
        <alttext lang="PT">Informação</alttext>
        <alttext lang="PL">Informacja</alttext>
        <alttext lang="NL">Infocenter</alttext>
        <alttext lang="RU">&#1048;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;</alttext>
        <alttext lang="AR">&#1605;&#1593;&#1604;&#1608;&#1605;&#1575;&#1578;</alttext>
        <description>Information and Communications</description>
        <description lang="DE">Informationen &amp; Kommunikation</description>
        <action>MENU info_menu.xml</action>
    </button>

    <button>
        <type>MENU_OPTICAL_DISKS</type>
        <text>Optical Disks</text>
        <text lang="IT">CD/DVD</text>
        <text lang="DE">CD/DVD</text>
        <text lang="IS">Geisladiskar</text>
        <text lang="NL">DVD/CD</text>
        <text lang="SV">Optiska skivor</text>
        <text lang="JA">&#12458;&#12503;&#12486;&#12451;&#12459;&#12523;&#12487;&#12451;&#12473;&#12463;</text>
        <text lang="FI">DVD ja CD</text>
        <text lang="ZH_TW">&#20809;&#30879;</text>
        <text lang="SL">CD/DVD</text>
        <text lang="ET">DVD ja CD</text>
        <text lang="ES">CD/DVD</text>
        <text lang="EN_GB">CD/DVD</text>
        <text lang="PT">CD/DVD</text>
        <text lang="RU">CD/DVD</text>
        <text lang="AR">&#1578;&#1588;&#1594;&#1610;&#1604; &#1573;&#1587;&#1591;&#1608;&#1575;&#1606;&#1575;&#1578;</text>
        <text lang="PL">Dyski optyczne</text>
        <text lang="HE">&#1491;&#1497;&#1505;&#1511;&#1497;&#1501; &#1488;&#1493;&#1508;&#1496;&#1497;&#1501;</text>
        <text lang="HU">CD/DVD</text>
        <description>Play or import CDs and DVDs</description>
        <description lang="DE">Abspielen/Importieren von CDs und DVDs</description>
        <action>MENU optical_menu.xml</action>
        <depends>mythmusic mythvideo mytharchive mythburn</depends>
    </button>

    <button>
        <type>TV_WATCH_TV</type>
        <text>Watch TV</text>
        <text lang="IT">Guarda la TV</text>
        <text lang="ES">Ver la TV</text>
        <text lang="NL">TV Kijken</text>
        <text lang="DE">Fernsehen</text>
        <text lang="IS">Horfa á sjónvarp</text>
        <text lang="PT">Ver Televisão</text>
        <text lang="SV">Se på TV</text>
        <text lang="JA">TV&#25918;&#36865;</text>
        <text lang="FI">Katso Televisiota</text>
        <text lang="ZH_TW">&#35264;&#30475;&#38651;&#35222;</text>
        <text lang="SL">Glej TV</text>
        <text lang="ET">Vaata telerit</text>
        <text lang="RU">&#1057;&#1084;&#1086;&#1090;&#1088;&#1077;&#1090;&#1100; &#1058;&#1042;</text>
        <text lang="AR">&#1588;&#1575;&#1607;&#1583; &#1575;&#1604;&#1578;&#1604;&#1601;&#1575;&#1586;</text>
        <text lang="PL">Ogl&#261;danie TV</text>
        <text lang="HE">&#1510;&#1508;&#1497;&#1492; &#1489;&#1496;&#1500;&#1493;&#1497;&#1494;&#1497;&#1492;</text>
        <text lang="HU">TV nézés</text>
        <description>Watch live television</description>
        <description lang="DE">Jetzt Fernsehen schauen</description>
        <action>TV_WATCH_LIVE</action>
    </button>

    <button>
        <type>MENU_UTILITIES_SETUP</type>
        <text>Utilities / Setup</text>
        <text lang="IT">Impostazioni</text>
        <text lang="ES">Configuración</text>
        <text lang="DE">Zubehör / Konfiguration</text>
        <text lang="IS">Uppsetning</text>
        <text lang="NL">Configuratie</text>
        <text lang="PT">Utensílios</text>
        <text lang="SV">Verktyg / Inställningar</text>
        <text lang="JA">&#35373;&#23450;</text>
        <text lang="FI">Oheis/Asetukset</text>
        <text lang="ZH_TW">&#24037;&#20855;/&#35373;&#23450;</text>
        <text lang="SL">Nastavitve</text>
        <text lang="ET">Utiliidid / sätted</text>
        <text lang="RU">&#1059;&#1090;&#1080;&#1083;&#1080;&#1090;&#1099; / &#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080;</text>
        <text lang="AR">&#1578;&#1590;&#1576;&#1610;&#1591;&#1575;&#1578;</text>
        <text lang="PL">Narz&#281;dzia / ustawienia</text>
        <text lang="HE">&#1506;&#1494;&#1512;&#1497;&#1501; / &#1492;&#1490;&#1491;&#1512;&#1493;&#1514;</text>
        <text lang="HU">Eszközök / Beállítások</text>
        <alttext lang="DE">Verschiedenes</alttext>
        <alttext lang="SV">Inställningar</alttext>
        <alttext lang="ET">Sätted</alttext>
        <alttext lang="RU">&#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080;</alttext>
        <alttext lang="AR">&#1578;&#1590;&#1576;&#1610;&#1591;&#1575;&#1578;</alttext>
        <description>Configure MythTV and plugins</description>
        <description lang="DE">MythTV und Plugins konfigurieren</description>
        <action>MENU util_menu.xml</action>
    </button>

    <!-- <button>
        <type>SHUTDOWN</type>
        <text>Shutdown</text>
        <text lang="SV">Avstängning</text>
        <text lang="NL">Uitschakelen</text>
        <text lang="DE">Beenden</text>
        <text lang="ET">Seiska</text>
        <text lang="PT">Gravações</text>
        <text lang="NL">Afsluiten</text>
        <text lang="RU">&#1047;&#1072;&#1074;&#1077;&#1088;&#1096;&#1077;&#1085;&#1080;&#1077; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099;</text>
        <text lang="PL">Zamknij system</text>
        <text lang="HE">&#1499;&#1497;&#1489;&#1493;&#1497;</text>
        <text lang="HU">Leállítás</text>
        <action>SHUTDOWN</action>
    </button> -->

</mythmenu>

```

---

### Post by uncle hammy on 2010-04-24
And I renamed default and defaultmenu folders, and mythfrontend fired up fine with this bizarre menu structure.  So it's obviously pulling it from somewhere strange, but the hwhy and where is eluding me.

---

### Post by uncle hammy on 2010-04-24
Well shiver me timbers.  Some sql'ing from the settings table for ```
value LIKE '%theme%'
```
turned up that MenuTheme had somehow got set to mediacenter.  CHanged it back, and it's normal!

---

