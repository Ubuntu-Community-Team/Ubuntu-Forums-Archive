---
title: "Java Not Working with Firefox 3.0.15 (Ubuntu 9.04)"
date: 2009-11-22
forum: Multimedia Software
---

### Post by newagelink on 2009-11-22
I have currently installed:
[LIST]
[*]Ubuntu 9.04 - the *Jaunty Jackalope*
[*]Firefox 3.0.15 (Firefox About window)
[*][COLOR="Red"]Java Console 6.0.02 (Firefox Extension window)[/COLOR] (removed)
[*]Sun Java 6 Runtime (Add/Remove Applications)
[*]Sun Java 6.0 Plugin (Add/Remove Applications)
[*][COLOR="Red"]OpenJDK Java 6 Web Start (Add/Remove Applications)[/COLOR] (removed)
[*][COLOR="Red"]OpenJDK Java 6 Runtime (Add/Remove Applications)[/COLOR] (removed)
[*]Java(TM) Plug-in 1.6.0_16 (Firefox Plugins window)
[/LIST]

I install Sun Java 6.0 Plugin from the Add/Remove Applications, finding it peculiar that its popularity is 1/5 stars.

I navigate to [Do I have Java?]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1") to see if it will "detect Java on [my] computer". I get the following error: > Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer. It wants me to download Version 6 Update 17.

Under the Firefox Plugins, I note that I have "IcedTea Java Web Browser Plugin" and "Java(TM) Plug-in 1.6.0_16" enabled. I disable the latter, which also disables the former: they are somehow linked to each other. When this is done, the Java test times out, redirecting me to [How do I test whether Java is working on my computer?]("http://www.java.com/en/download/help/testvm.xml"). With these add-ons disabled, it appears equivalent to disabling Java for Firefox: indeed, I found the "Enable Java" box unchecked, and checking it enabled those same two plugins.

I uninstall the "Ubufox extension for Firefox" from the Add/Remove Applications (also 1/5 star Popularity), since I can't figure out what it does, and maybe it's the problem.

I download jre-6u17-linux-i586.bin, move it to /home/daniel/programs, look at [Installing .bin in Ubuntu]("http://www.linuxforums.org/forum/ubuntu-help/63528-installing-bin-ubuntu.html") and run the commands: ```
chmod 755 jre-6u17-linux-i586.bin
./jre-6u17-linux-i586.bin
```

I successfully install it -- the remainder of the output:
>  extracting: jre1.6.0_17/lib/zi/Asia/Kabul  
 extracting: jre1.6.0_17/lib/zi/Asia/Qatar  
 extracting: jre1.6.0_17/lib/zi/Asia/Pontianak  
  inflating: jre1.6.0_17/lib/zi/Asia/Aqtobe  
  inflating: jre1.6.0_17/lib/zi/Asia/Nicosia  
 extracting: jre1.6.0_17/lib/zi/Asia/Makassar  
  inflating: jre1.6.0_17/lib/zi/Asia/Tashkent  
  inflating: jre1.6.0_17/lib/zi/Asia/Manila  
 extracting: jre1.6.0_17/lib/zi/Asia/Phnom_Penh  
 extracting: jre1.6.0_17/lib/zi/Asia/Jakarta  
 extracting: jre1.6.0_17/lib/zi/Asia/Bahrain  
  inflating: jre1.6.0_17/lib/zi/Asia/Ashgabat  
  inflating: jre1.6.0_17/lib/zi/Asia/Macau  
  inflating: jre1.6.0_17/lib/zi/Asia/Jerusalem  
  inflating: jre1.6.0_17/lib/zi/Asia/Amman  
  inflating: jre1.6.0_17/lib/zi/Asia/Baku  
  inflating: jre1.6.0_17/lib/zi/Asia/Seoul  
 extracting: jre1.6.0_17/lib/zi/Asia/Rangoon  
 extracting: jre1.6.0_17/lib/zi/Asia/Dubai  
  inflating: jre1.6.0_17/lib/zi/Asia/Harbin  
  inflating: jre1.6.0_17/lib/zi/Asia/Qyzylorda  
  inflating: jre1.6.0_17/lib/zi/Asia/Chongqing  
  inflating: jre1.6.0_17/lib/zi/Asia/Samarkand  
 extracting: jre1.6.0_17/lib/zi/Asia/Thimphu  
  inflating: jre1.6.0_17/lib/zi/Asia/Urumqi  
 extracting: jre1.6.0_17/lib/zi/Asia/Kathmandu  
 extracting: jre1.6.0_17/lib/zi/Asia/Riyadh  
 extracting: jre1.6.0_17/lib/zi/Asia/Aden  
  inflating: jre1.6.0_17/lib/zi/Asia/Gaza  
 extracting: jre1.6.0_17/lib/zi/Asia/Jayapura  
  inflating: jre1.6.0_17/lib/zi/Asia/Beirut  
  inflating: jre1.6.0_17/lib/zi/Asia/Choibalsan  
 extracting: jre1.6.0_17/lib/zi/Asia/Kuwait  
  inflating: jre1.6.0_17/lib/zi/Asia/Ulaanbaatar  
 extracting: jre1.6.0_17/lib/zi/Asia/Vientiane  
  inflating: jre1.6.0_17/lib/zi/Asia/Tehran  
 extracting: jre1.6.0_17/lib/zi/Asia/Kuala_Lumpur  
 extracting: jre1.6.0_17/lib/zi/Asia/Brunei  
  inflating: jre1.6.0_17/lib/zi/Asia/Almaty  
 extracting: jre1.6.0_17/lib/zi/Asia/Ho_Chi_Minh  
  inflating: jre1.6.0_17/lib/zi/Asia/Aqtau  
  inflating: jre1.6.0_17/lib/zi/Asia/Tbilisi  
  inflating: jre1.6.0_17/lib/zi/Asia/Baghdad  
 extracting: jre1.6.0_17/lib/zi/Asia/Kolkata  
 extracting: jre1.6.0_17/lib/zi/Asia/Dhaka  
  inflating: jre1.6.0_17/lib/zi/Asia/Pyongyang  
 extracting: jre1.6.0_17/lib/zi/Asia/Singapore  
  inflating: jre1.6.0_17/lib/zi/Asia/Dushanbe  
  inflating: jre1.6.0_17/lib/zi/Asia/Yakutsk  
  inflating: jre1.6.0_17/lib/zi/Asia/Magadan  
  inflating: jre1.6.0_17/lib/zi/Asia/Yekaterinburg  
  inflating: jre1.6.0_17/lib/zi/Asia/Vladivostok  
  inflating: jre1.6.0_17/lib/zi/Asia/Anadyr  
  inflating: jre1.6.0_17/lib/zi/Asia/Omsk  
  inflating: jre1.6.0_17/lib/zi/Asia/Novosibirsk  
  inflating: jre1.6.0_17/lib/zi/Asia/Sakhalin  
  inflating: jre1.6.0_17/lib/zi/Asia/Krasnoyarsk  
  inflating: jre1.6.0_17/lib/zi/Asia/Irkutsk  
  inflating: jre1.6.0_17/lib/zi/Asia/Kamchatka  
  inflating: jre1.6.0_17/lib/zi/Asia/Riyadh87  
  inflating: jre1.6.0_17/lib/zi/Asia/Riyadh88  
  inflating: jre1.6.0_17/lib/zi/Asia/Riyadh89  
   creating: jre1.6.0_17/lib/zi/Atlantic/
  inflating: jre1.6.0_17/lib/zi/Atlantic/St_Helena  
 extracting: jre1.6.0_17/lib/zi/Atlantic/Cape_Verde  
  inflating: jre1.6.0_17/lib/zi/Atlantic/Faroe  
  inflating: jre1.6.0_17/lib/zi/Atlantic/Reykjavik  
  inflating: jre1.6.0_17/lib/zi/Atlantic/Canary  
  inflating: jre1.6.0_17/lib/zi/Atlantic/Azores  
  inflating: jre1.6.0_17/lib/zi/Atlantic/Madeira  
  inflating: jre1.6.0_17/lib/zi/Atlantic/Bermuda  
  inflating: jre1.6.0_17/lib/zi/Atlantic/South_Georgia  
  inflating: jre1.6.0_17/lib/zi/Atlantic/Stanley  
   creating: jre1.6.0_17/lib/zi/Australia/
  inflating: jre1.6.0_17/lib/zi/Australia/Lindeman  
  inflating: jre1.6.0_17/lib/zi/Australia/Hobart  
  inflating: jre1.6.0_17/lib/zi/Australia/Melbourne  
  inflating: jre1.6.0_17/lib/zi/Australia/Perth  
  inflating: jre1.6.0_17/lib/zi/Australia/Sydney  
  inflating: jre1.6.0_17/lib/zi/Australia/Lord_Howe  
  inflating: jre1.6.0_17/lib/zi/Australia/Currie  
  inflating: jre1.6.0_17/lib/zi/Australia/Brisbane  
  inflating: jre1.6.0_17/lib/zi/Australia/Broken_Hill  
  inflating: jre1.6.0_17/lib/zi/Australia/Darwin  
  inflating: jre1.6.0_17/lib/zi/Australia/Eucla  
  inflating: jre1.6.0_17/lib/zi/Australia/Adelaide  
  inflating: jre1.6.0_17/lib/zi/CET  
  inflating: jre1.6.0_17/lib/zi/CST6CDT  
  inflating: jre1.6.0_17/lib/zi/EET  
 extracting: jre1.6.0_17/lib/zi/EST  
  inflating: jre1.6.0_17/lib/zi/EST5EDT  
   creating: jre1.6.0_17/lib/zi/Etc/
  inflating: jre1.6.0_17/lib/zi/Etc/UTC  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-14  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT-13  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-12  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT-11  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-10  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-1  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT+11  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT+12  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT-5  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT+7  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT+10  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-4  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT+6  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-3  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT+5  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-2  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT+4  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT-9  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT+3  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-8  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT+2  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT-7  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT+1  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT-6  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT+8  
 extracting: jre1.6.0_17/lib/zi/Etc/GMT+9  
  inflating: jre1.6.0_17/lib/zi/Etc/UCT  
  inflating: jre1.6.0_17/lib/zi/Etc/GMT  
   creating: jre1.6.0_17/lib/zi/Europe/
  inflating: jre1.6.0_17/lib/zi/Europe/Samara  
  inflating: jre1.6.0_17/lib/zi/Europe/Sofia  
  inflating: jre1.6.0_17/lib/zi/Europe/Monaco  
  inflating: jre1.6.0_17/lib/zi/Europe/Gibraltar  
  inflating: jre1.6.0_17/lib/zi/Europe/Vienna  
  inflating: jre1.6.0_17/lib/zi/Europe/Kaliningrad  
  inflating: jre1.6.0_17/lib/zi/Europe/Malta  
  inflating: jre1.6.0_17/lib/zi/Europe/Madrid  
  inflating: jre1.6.0_17/lib/zi/Europe/Volgograd  
  inflating: jre1.6.0_17/lib/zi/Europe/Minsk  
  inflating: jre1.6.0_17/lib/zi/Europe/Vilnius  
  inflating: jre1.6.0_17/lib/zi/Europe/Lisbon  
  inflating: jre1.6.0_17/lib/zi/Europe/Riga  
  inflating: jre1.6.0_17/lib/zi/Europe/Zurich  
  inflating: jre1.6.0_17/lib/zi/Europe/Luxembourg  
  inflating: jre1.6.0_17/lib/zi/Europe/Dublin  
  inflating: jre1.6.0_17/lib/zi/Europe/Brussels  
  inflating: jre1.6.0_17/lib/zi/Europe/Zaporozhye  
  inflating: jre1.6.0_17/lib/zi/Europe/Simferopol  
  inflating: jre1.6.0_17/lib/zi/Europe/Oslo  
  inflating: jre1.6.0_17/lib/zi/Europe/Rome  
  inflating: jre1.6.0_17/lib/zi/Europe/Tirane  
  inflating: jre1.6.0_17/lib/zi/Europe/Istanbul  
  inflating: jre1.6.0_17/lib/zi/Europe/Copenhagen  
  inflating: jre1.6.0_17/lib/zi/Europe/Bucharest  
  inflating: jre1.6.0_17/lib/zi/Europe/Helsinki  
  inflating: jre1.6.0_17/lib/zi/Europe/Tallinn  
  inflating: jre1.6.0_17/lib/zi/Europe/Amsterdam  
  inflating: jre1.6.0_17/lib/zi/Europe/Athens  
  inflating: jre1.6.0_17/lib/zi/Europe/Uzhgorod  
  inflating: jre1.6.0_17/lib/zi/Europe/Stockholm  
  inflating: jre1.6.0_17/lib/zi/Europe/Berlin  
  inflating: jre1.6.0_17/lib/zi/Europe/Andorra  
  inflating: jre1.6.0_17/lib/zi/Europe/Chisinau  
  inflating: jre1.6.0_17/lib/zi/Europe/Budapest  
  inflating: jre1.6.0_17/lib/zi/Europe/Paris  
  inflating: jre1.6.0_17/lib/zi/Europe/Vaduz  
  inflating: jre1.6.0_17/lib/zi/Europe/Prague  
  inflating: jre1.6.0_17/lib/zi/Europe/Kiev  
  inflating: jre1.6.0_17/lib/zi/Europe/Warsaw  
  inflating: jre1.6.0_17/lib/zi/Europe/Belgrade  
  inflating: jre1.6.0_17/lib/zi/Europe/London  
  inflating: jre1.6.0_17/lib/zi/Europe/Moscow  
  inflating: jre1.6.0_17/lib/zi/GMT  
  inflating: jre1.6.0_17/lib/zi/HST  
   creating: jre1.6.0_17/lib/zi/Indian/
 extracting: jre1.6.0_17/lib/zi/Indian/Mahe  
 extracting: jre1.6.0_17/lib/zi/Indian/Comoro  
 extracting: jre1.6.0_17/lib/zi/Indian/Antananarivo  
 extracting: jre1.6.0_17/lib/zi/Indian/Mayotte  
  inflating: jre1.6.0_17/lib/zi/Indian/Mauritius  
 extracting: jre1.6.0_17/lib/zi/Indian/Reunion  
 extracting: jre1.6.0_17/lib/zi/Indian/Kerguelen  
 extracting: jre1.6.0_17/lib/zi/Indian/Maldives  
 extracting: jre1.6.0_17/lib/zi/Indian/Chagos  
 extracting: jre1.6.0_17/lib/zi/Indian/Christmas  
 extracting: jre1.6.0_17/lib/zi/Indian/Cocos  
  inflating: jre1.6.0_17/lib/zi/MET  
 extracting: jre1.6.0_17/lib/zi/MST  
  inflating: jre1.6.0_17/lib/zi/MST7MDT  
  inflating: jre1.6.0_17/lib/zi/PST8PDT  
   creating: jre1.6.0_17/lib/zi/Pacific/
  inflating: jre1.6.0_17/lib/zi/Pacific/Kiritimati  
  inflating: jre1.6.0_17/lib/zi/Pacific/Funafuti  
  inflating: jre1.6.0_17/lib/zi/Pacific/Tarawa  
  inflating: jre1.6.0_17/lib/zi/Pacific/Majuro  
 extracting: jre1.6.0_17/lib/zi/Pacific/Pitcairn  
 extracting: jre1.6.0_17/lib/zi/Pacific/Kosrae  
  inflating: jre1.6.0_17/lib/zi/Pacific/Efate  
  inflating: jre1.6.0_17/lib/zi/Pacific/Wallis  
 extracting: jre1.6.0_17/lib/zi/Pacific/Guadalcanal  
 extracting: jre1.6.0_17/lib/zi/Pacific/Niue  
 extracting: jre1.6.0_17/lib/zi/Pacific/Pago_Pago  
  inflating: jre1.6.0_17/lib/zi/Pacific/Tongatapu  
  inflating: jre1.6.0_17/lib/zi/Pacific/Kwajalein  
 extracting: jre1.6.0_17/lib/zi/Pacific/Marquesas  
  inflating: jre1.6.0_17/lib/zi/Pacific/Enderbury  
  inflating: jre1.6.0_17/lib/zi/Pacific/Wake  
 extracting: jre1.6.0_17/lib/zi/Pacific/Tahiti  
  inflating: jre1.6.0_17/lib/zi/Pacific/Rarotonga  
  inflating: jre1.6.0_17/lib/zi/Pacific/Fiji  
 extracting: jre1.6.0_17/lib/zi/Pacific/Ponape  
  inflating: jre1.6.0_17/lib/zi/Pacific/Auckland  
  inflating: jre1.6.0_17/lib/zi/Pacific/Norfolk  
  inflating: jre1.6.0_17/lib/zi/Pacific/Johnston  
 extracting: jre1.6.0_17/lib/zi/Pacific/Midway  
  inflating: jre1.6.0_17/lib/zi/Pacific/Guam  
 extracting: jre1.6.0_17/lib/zi/Pacific/Palau  
 extracting: jre1.6.0_17/lib/zi/Pacific/Nauru  
 extracting: jre1.6.0_17/lib/zi/Pacific/Gambier  
 extracting: jre1.6.0_17/lib/zi/Pacific/Apia  
  inflating: jre1.6.0_17/lib/zi/Pacific/Chatham  
  inflating: jre1.6.0_17/lib/zi/Pacific/Port_Moresby  
  inflating: jre1.6.0_17/lib/zi/Pacific/Saipan  
  inflating: jre1.6.0_17/lib/zi/Pacific/Noumea  
 extracting: jre1.6.0_17/lib/zi/Pacific/Fakaofo  
  inflating: jre1.6.0_17/lib/zi/Pacific/Truk  
 extracting: jre1.6.0_17/lib/zi/Pacific/Honolulu  
  inflating: jre1.6.0_17/lib/zi/Pacific/Easter  
 extracting: jre1.6.0_17/lib/zi/Pacific/Galapagos  
   creating: jre1.6.0_17/lib/zi/SystemV/
  inflating: jre1.6.0_17/lib/zi/SystemV/PST8PDT  
 extracting: jre1.6.0_17/lib/zi/SystemV/YST9  
  inflating: jre1.6.0_17/lib/zi/SystemV/CST6CDT  
  inflating: jre1.6.0_17/lib/zi/SystemV/CST6  
 extracting: jre1.6.0_17/lib/zi/SystemV/MST7  
  inflating: jre1.6.0_17/lib/zi/SystemV/YST9YDT  
  inflating: jre1.6.0_17/lib/zi/SystemV/HST10  
 extracting: jre1.6.0_17/lib/zi/SystemV/EST5  
  inflating: jre1.6.0_17/lib/zi/SystemV/PST8  
  inflating: jre1.6.0_17/lib/zi/SystemV/AST4ADT  
  inflating: jre1.6.0_17/lib/zi/SystemV/AST4  
  inflating: jre1.6.0_17/lib/zi/SystemV/MST7MDT  
  inflating: jre1.6.0_17/lib/zi/SystemV/EST5EDT  
  inflating: jre1.6.0_17/lib/zi/WET  
  inflating: jre1.6.0_17/lib/zi/ZoneInfoMappings  
  inflating: jre1.6.0_17/lib/fontconfig.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.2.1.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.3.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.4.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.Sun.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.Turbo.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.SuSE.properties.src  
  inflating: jre1.6.0_17/lib/fontconfig.bfc  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.bfc  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.2.1.bfc  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.3.bfc  
  inflating: jre1.6.0_17/lib/fontconfig.RedHat.4.bfc  
  inflating: jre1.6.0_17/lib/fontconfig.Sun.bfc  
  inflating: jre1.6.0_17/lib/fontconfig.Turbo.bfc  
  inflating: jre1.6.0_17/lib/fontconfig.SuSE.bfc  
   creating: jre1.6.0_17/lib/cmm/
  inflating: jre1.6.0_17/lib/cmm/sRGB.pf  
  inflating: jre1.6.0_17/lib/cmm/GRAY.pf  
  inflating: jre1.6.0_17/lib/cmm/CIEXYZ.pf  
  inflating: jre1.6.0_17/lib/cmm/PYCC.pf  
  inflating: jre1.6.0_17/lib/cmm/LINEAR_RGB.pf  
  inflating: jre1.6.0_17/lib/plugin.pack  
   creating: jre1.6.0_17/lib/management/
  inflating: jre1.6.0_17/lib/management/management.properties  
  inflating: jre1.6.0_17/lib/management/snmp.acl.template  
  inflating: jre1.6.0_17/lib/management/jmxremote.password.template  
  inflating: jre1.6.0_17/lib/management/jmxremote.access  
  inflating: jre1.6.0_17/lib/meta-index  
   creating: jre1.6.0_17/lib/im/
  inflating: jre1.6.0_17/lib/im/indicim.jar  
  inflating: jre1.6.0_17/lib/im/thaiim.jar  
   creating: jre1.6.0_17/lib/servicetag/
  inflating: jre1.6.0_17/lib/servicetag/jdk_header.png  
  inflating: jre1.6.0_17/lib/alt-rt.jar  
   creating: jre1.6.0_17/lib/desktop/
   creating: jre1.6.0_17/lib/desktop/icons/
   creating: jre1.6.0_17/lib/desktop/icons/hicolor/
   creating: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/
   creating: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/apps/
  inflating: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/apps/sun-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/apps/sun-javaws.png  
  inflating: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/mimetypes/
 extracting: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/mimetypes/gnome-mime-text-x-java.png  
 extracting: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/mimetypes/gnome-mime-application-x-java-archive.png  
 extracting: jre1.6.0_17/lib/desktop/icons/hicolor/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/
   creating: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/apps/
  inflating: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/apps/sun-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/apps/sun-javaws.png  
  inflating: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/mimetypes/
 extracting: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/mimetypes/gnome-mime-text-x-java.png  
 extracting: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-java-archive.png  
 extracting: jre1.6.0_17/lib/desktop/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrast/
   creating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/
   creating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/apps/
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/apps/sun-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/apps/sun-javaws.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/mimetypes/
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/mimetypes/gnome-mime-text-x-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/mimetypes/gnome-mime-application-x-java-archive.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/
   creating: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/apps/
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/apps/sun-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/apps/sun-javaws.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/mimetypes/
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/mimetypes/gnome-mime-text-x-java.png  
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/mimetypes/gnome-mime-application-x-java-archive.png  
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrast/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/
   creating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/
   creating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/apps/
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/apps/sun-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/apps/sun-javaws.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/mimetypes/
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/mimetypes/gnome-mime-text-x-java.png  
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/mimetypes/gnome-mime-application-x-java-archive.png  
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/
   creating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/apps/
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/apps/sun-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/apps/sun-javaws.png  
  inflating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/mimetypes/
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/mimetypes/gnome-mime-text-x-java.png  
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/mimetypes/gnome-mime-application-x-java-archive.png  
 extracting: jre1.6.0_17/lib/desktop/icons/HighContrastInverse/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/icons/LowContrast/
   creating: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/
   creating: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/apps/
 extracting: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/apps/sun-java.png  
 extracting: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/apps/sun-javaws.png  
 extracting: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/mimetypes/
 extracting: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/mimetypes/gnome-mime-text-x-java.png  
 extracting: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/mimetypes/gnome-mime-application-x-java-archive.png  
 extracting: jre1.6.0_17/lib/desktop/icons/LowContrast/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/
   creating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/apps/
  inflating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/apps/sun-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/apps/sun-javaws.png  
  inflating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/apps/sun-jcontrol.png  
   creating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/mimetypes/
  inflating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/mimetypes/gnome-mime-text-x-java.png  
  inflating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/mimetypes/gnome-mime-application-x-java-archive.png  
  inflating: jre1.6.0_17/lib/desktop/icons/LowContrast/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png  
   creating: jre1.6.0_17/lib/desktop/applications/
  inflating: jre1.6.0_17/lib/desktop/applications/sun-java.desktop  
  inflating: jre1.6.0_17/lib/desktop/applications/sun-javaws.desktop  
  inflating: jre1.6.0_17/lib/desktop/applications/sun_java.desktop  
   creating: jre1.6.0_17/lib/desktop/mime/
   creating: jre1.6.0_17/lib/desktop/mime/packages/
  inflating: jre1.6.0_17/lib/desktop/mime/packages/x-java-archive.xml  
  inflating: jre1.6.0_17/lib/desktop/mime/packages/x-java-jnlp-file.xml  
   creating: jre1.6.0_17/lib/locale/
   creating: jre1.6.0_17/lib/locale/de/
   creating: jre1.6.0_17/lib/locale/de/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/de/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/es/
   creating: jre1.6.0_17/lib/locale/es/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/es/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/fr/
   creating: jre1.6.0_17/lib/locale/fr/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/fr/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/it/
   creating: jre1.6.0_17/lib/locale/it/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/it/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/ja/
   creating: jre1.6.0_17/lib/locale/ja/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/ja/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/ko/
   creating: jre1.6.0_17/lib/locale/ko/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/ko/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/ko.UTF-8/
   creating: jre1.6.0_17/lib/locale/ko.UTF-8/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/ko.UTF-8/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/sv/
   creating: jre1.6.0_17/lib/locale/sv/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/sv/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/zh/
   creating: jre1.6.0_17/lib/locale/zh/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/zh/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/zh.GBK/
   creating: jre1.6.0_17/lib/locale/zh.GBK/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/zh.GBK/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/zh_TW/
   creating: jre1.6.0_17/lib/locale/zh_TW/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/zh_TW/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/zh_TW.BIG5/
   creating: jre1.6.0_17/lib/locale/zh_TW.BIG5/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/zh_TW.BIG5/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/locale/zh_HK.BIG5HK/
   creating: jre1.6.0_17/lib/locale/zh_HK.BIG5HK/LC_MESSAGES/
  inflating: jre1.6.0_17/lib/locale/zh_HK.BIG5HK/LC_MESSAGES/sunw_java_plugin.mo  
   creating: jre1.6.0_17/lib/deploy/
  inflating: jre1.6.0_17/lib/deploy/ffjcext.zip  
  inflating: jre1.6.0_17/lib/deploy/splash.gif  
  inflating: jre1.6.0_17/lib/deploy/messages.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_zh_TW.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_de.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_es.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_fr.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_it.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_ja.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_ko.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_sv.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_zh_CN.properties  
  inflating: jre1.6.0_17/lib/deploy/messages_zh_HK.properties  
  inflating: jre1.6.0_17/lib/deploy/java-icon.ico  
  inflating: jre1.6.0_17/lib/javaws.pack  
  inflating: jre1.6.0_17/lib/deploy.pack  
  inflating: jre1.6.0_17/lib/jsse.pack  
  inflating: jre1.6.0_17/lib/charsets.pack  
  inflating: jre1.6.0_17/COPYRIGHT   
  inflating: jre1.6.0_17/Welcome.html  
  inflating: jre1.6.0_17/README      
  inflating: jre1.6.0_17/LICENSE     
  inflating: jre1.6.0_17/THIRDPARTYLICENSEREADME.txt  
   creating: jre1.6.0_17/man/
   creating: jre1.6.0_17/man/man1/
  inflating: jre1.6.0_17/man/man1/java.1  
  inflating: jre1.6.0_17/man/man1/keytool.1  
  inflating: jre1.6.0_17/man/man1/rmid.1  
  inflating: jre1.6.0_17/man/man1/rmiregistry.1  
  inflating: jre1.6.0_17/man/man1/tnameserv.1  
  inflating: jre1.6.0_17/man/man1/servertool.1  
  inflating: jre1.6.0_17/man/man1/orbd.1  
  inflating: jre1.6.0_17/man/man1/policytool.1  
  inflating: jre1.6.0_17/man/man1/pack200.1  
  inflating: jre1.6.0_17/man/man1/unpack200.1  
  inflating: jre1.6.0_17/man/man1/javaws.1  
    linking: jre1.6.0_17/man/ja      -> ja_JP.eucJP 
   creating: jre1.6.0_17/man/ja_JP.eucJP/
   creating: jre1.6.0_17/man/ja_JP.eucJP/man1/
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/java.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/keytool.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/rmid.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/rmiregistry.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/tnameserv.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/servertool.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/orbd.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/policytool.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/pack200.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/unpack200.1  
  inflating: jre1.6.0_17/man/ja_JP.eucJP/man1/javaws.1  
   creating: jre1.6.0_17/plugin/
   creating: jre1.6.0_17/plugin/i386/
   creating: jre1.6.0_17/plugin/i386/ns7/
  inflating: jre1.6.0_17/plugin/i386/ns7/libjavaplugin_oji.so  
   creating: jre1.6.0_17/plugin/i386/ns7-gcc29/
  inflating: jre1.6.0_17/plugin/i386/ns7-gcc29/libjavaplugin_oji.so  
   creating: jre1.6.0_17/plugin/desktop/
 extracting: jre1.6.0_17/plugin/desktop/sun_java.png  
  inflating: jre1.6.0_17/plugin/desktop/sun_java.desktop  
   creating: jre1.6.0_17/javaws/
    linking: jre1.6.0_17/javaws/javaws  -> ../bin/javaws 
Creating jre1.6.0_17/lib/rt.jar
Creating jre1.6.0_17/lib/jsse.jar
Creating jre1.6.0_17/lib/charsets.jar
Creating jre1.6.0_17/lib/ext/localedata.jar
Creating jre1.6.0_17/lib/plugin.jar
Creating jre1.6.0_17/lib/javaws.jar
Creating jre1.6.0_17/lib/deploy.jar
 
Done.

But there is no change in the response from [Do I have Java?]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1").

I uninstall "Icedtea Java Plugin" from Add/Remove Applications. I navigate to [Do I have Java?]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1") to see if it will "detect Java on [my] computer". I get the following error: > Oops! You don't have the recommended Java installed.
**Your Java version is Version 6 Update 16.** It wants me to download Version 6 Update 17.

I uninstall "Sun Java 6.0 Plugin" from Add/Remove Applications. Firefox then prompts me at the page [Do I have Java?]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1") that I need to install additional plugins, so I close Firefox and reinstall it.

I reinstall "jre-6u17-linux-i586.bin", overwriting the previous installation. I close and reopen Firefox, and clear Browsing History, Saved Form and Search History, Cache and Authenticated Sessions. I close and reopen Firefox. No change: it still says I have Version 6 Update 16.

What do I do now?

Please help me; I want to play Chess at pogo.com and they require Java. :( I am trying to learn how to make computers do what I want, and I am so very discouraged, because it seems even when everything is installed, it still doesn't work.

**EDIT**: At the instruction of people who read this thread (in Yahoo Chat room), I 
[LIST=1]
[*]uninstalled Java Console 6.0.02
[*]created folder "plugins" at /home/daniel/.mozilla/firefox
[*]copied file "/home/daniel/programs/jre1.6.0_17/plugin/i386/ns7/libjavaplugin_oji.so" to it
[*]uninstalled openjdk-6-jre packages (Synaptic Package Manager)
[*]uninstalled default-jre packages
[*]uninstalled icedtea-6-jre-cacao
[/LIST]

---

### Post by newagelink on 2009-11-26
Apparently uninstalling the excess software, and possibly adding the plugins folder and copy/pasting the file into it as instructed -- some combination fixed the problem; I apparently only needed to reboot my computer: the Java applet is now working with Chess at pogo.com.

Thanks yahoo chat people! :)

---

