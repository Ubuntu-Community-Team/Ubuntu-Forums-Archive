---
title: "Help me configure xorg.conf"
date: 2010-03-31
forum: Multimedia Software
---

### Post by espvar on 2010-03-31
Can anyone help me configure xorg.conf?

This is my setup:
Graphics: [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2963](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2963)

screen 1: 1680x1050 [http://tom.viewsonic.com/pdf/us_eng/products/Q201wb-1_Jan_2008.pdf](http://tom.viewsonic.com/pdf/us_eng/products/Q201wb-1_Jan_2008.pdf)

screen 2: 1280x720[http://www.dwe.co.kr/lib/file_down_hit.asp?server_dir=D:\Inetpub\wwwroot\upload\download_en&file_name=SL-500P_eng_A5_DMP3994500(7).pdf&table_name=TB_DOWNLOAD_EN_BOARD&hitType=M&seq=9369]("http://www.dwe.co.kr/lib/file_down_hit.asp?server_dir=D:%5CInetpub%5Cwwwroot%5Cupload%5Cdownload_en&file_name=SL-500P_eng_A5_DMP3994500%287%29.pdf&table_name=TB_DOWNLOAD_EN_BOARD&hitType=M&seq=9369")
 
  and 1024x768[http://www.superwarehouse.com/IBM_ThinkVision_L150p_Black_15_LCD_Monitor/6636HB1/ps/313103](http://www.superwarehouse.com/IBM_ThinkVision_L150p_Black_15_LCD_Monitor/6636HB1/ps/313103)

 screen 2 is splitted into two screens with a HDMI-splitter so that the extended desktop are displayed on both screens.

Ubuntu is unable to detect my screens correctly and gives me only 1024x768 res. on both screen 1 and 2. After using a xorg.conf i found on another forum I can set the resolution to 1280x720 on screen 1 and 1024x768 on screen 2. What i want is 1680x1050 on screen 1 and 1280x720 on the two screens connected to screen 2.
This is my present xorg.conf:
```
Section "Device"
Identifier "Configured Video Device"
EndSection

Section  "Monitor"
Identifier "Configured Monitor"
HorizSync 28-40
VertRefresh  43-60
modeline "800×600@56" 36.0 800 824 896 1024 600 601 603 625
modeline  "800×600@72" 50.0 800 856 976 1040 600 637 643 666
modeline  "800×600@75" 49.5 800 816 896 1056 600 601 604 625
modeline  "800×600@60" 40.0 800 840 968 1056 600 601 605 628
Modeline  "1024×768@60" 64.56 1024 1056 1296 1328 768 783 791 807
Modeline  "1152×720@60" 66.75 1152 1184 1432 1464 720 735 742 757
modeline  "1152×768@54" 64.995 1152 1178 1314 1472 768 771 777 806
Modeline  "1280×800@60" 83.91 1280 1312 1624 1656 800 816 824 841
modeline  "1280×854" 80.0 1280 1309 1460 1636 854 857 864 896
modeline  "1280×768@60" 80.14 1280 1344 1480 1680 768 769 772 795
modeline  "1280×720@60" 74.48 1280 1336 1472 1664 720 721 724 746
modeline  "1280×800@75" 107.21 1280 1360 1496 1712 800 801 804 835
modeline  "1280×768@75" 102.98 1280 1360 1496 1712 768 769 772 802
modeline  "1280×720@50" 60.47 1280 1328 1456 1632 720 721 724 741
modeline  "1280×800@60" 83.46 1280 1344 1480 1680 800 801 804 828
modeline  "1440×900@75" 136.49 1440 1536 1688 1936 900 901 904 940
modeline  "1440×900@60" 106.47 1440 1520 1672 1904 900 901 904 932
modeline  "1600×1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060
modeline  "1680×1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087
modeline  "1680×1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096
modeline  "1920×1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242

EndSection

Section  "Screen"
Identifier "Default Screen"
Device "Configured Video  Device"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection  "Display"
Depth 24
Modes "1440×900@60" "1600×1024@60"  "1440×900@75" "1680×1050@60" "1280×800@60" "1680×1050@75" "1280×720@50"  "1920×1200@60" "1280×768@75" "1280×800@75" "1280×720@60" "1280×768@60"  "1280×800@60" "1280×854" "1152×720@60" "1152×768@54" "1024×768@60"  "800×600@60" "800×600@75" "800×600@72" "800×600@56"
EndSubSection
EndSection

Section  "ServerLayout"
Identifier "Default Layout"
Screen "Default  Screen"
EndSection
```

---

