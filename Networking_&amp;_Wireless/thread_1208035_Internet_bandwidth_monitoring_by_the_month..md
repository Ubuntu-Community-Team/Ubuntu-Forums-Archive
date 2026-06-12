---
title: "Internet bandwidth monitoring by the month."
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by Avuton Olrich on 2009-07-08
Hello,

Long story:
This is probably a pretty common thing, Comcast called said I was using too much bandwidth, I've been capped to 250GB/month. I have a NAT for all internet traffic anyhow.

Short question:
Does anyone know of a good network monitoring tool I can use to find out my monthly usage?

---

### Post by gpsmikey on 2009-07-08
Depending on what router you are using -- for the Linksys WRT54 series (some versions anyway), you can load with "Tomato".  One of the things it does is show daily, weekly and monthly bandwidth etc.
[http://en.wikipedia.org/wiki/Tomato_%28firmware%29](http://en.wikipedia.org/wiki/Tomato_%28firmware%29)

mikey

---

### Post by Avuton Olrich on 2009-07-10
Guess I should have mentioned I'm using Ubuntu as a router. Thanks!.

---

### Post by Avuton Olrich on 2009-07-17
Hate to bump this but I really need an answer. There has to be something like this with so many of us internet users who are capped.

---

### Post by gombadi on 2009-07-17
On your Ubuntu router install the vnstat package and configure it.

Each day or whenever you want you can run the vnstat command and get this type of output.

```

human@ds2-uk:~$ vnstat -d

 eth0  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   19.06.      3.52 GB  |  112.45 GB  |  115.97 GB   :::::::::::::::
   20.06.      3.04 GB  |   91.15 GB  |   94.18 GB   ::::::::::::
   21.06.      3.19 GB  |   80.51 GB  |   83.71 GB   :::::::::::
   22.06.      3.58 GB  |  118.72 GB  |  122.30 GB   ::::::::::::::::
   23.06.      4.73 GB  |  155.46 GB  |  160.19 GB   %::::::::::::::::::::
   24.06.      4.16 GB  |  137.72 GB  |  141.88 GB   %:::::::::::::::::
   25.06.      4.10 GB  |  131.57 GB  |  135.67 GB   %:::::::::::::::::
   26.06.      4.27 GB  |  140.32 GB  |  144.59 GB   %::::::::::::::::::
   27.06.      3.86 GB  |  114.58 GB  |  118.44 GB   :::::::::::::::
   28.06.      3.49 GB  |  105.36 GB  |  108.85 GB   ::::::::::::::
   29.06.      3.90 GB  |  124.41 GB  |  128.31 GB   %::::::::::::::::
   30.06.      4.45 GB  |  136.01 GB  |  140.46 GB   %:::::::::::::::::
   01.07.      4.11 GB  |  129.27 GB  |  133.38 GB   %::::::::::::::::
   02.07.     14.01 GB  |  160.89 GB  |  174.90 GB   %%:::::::::::::::::::::
   03.07.      5.10 GB  |  161.91 GB  |  167.01 GB   %:::::::::::::::::::::
   04.07.      4.68 GB  |  146.71 GB  |  151.39 GB   %:::::::::::::::::::
   05.07.      4.24 GB  |  133.91 GB  |  138.15 GB   %:::::::::::::::::
   06.07.      3.90 GB  |  125.20 GB  |  129.10 GB   %::::::::::::::::
   07.07.      5.09 GB  |  167.30 GB  |  172.39 GB   %:::::::::::::::::::::
   08.07.      4.98 GB  |  162.46 GB  |  167.44 GB   %:::::::::::::::::::::
   09.07.      5.01 GB  |  167.52 GB  |  172.53 GB   %:::::::::::::::::::::
   10.07.      5.41 GB  |  182.70 GB  |  188.11 GB   %::::::::::::::::::::::::
   11.07.      5.03 GB  |  172.46 GB  |  177.49 GB   %::::::::::::::::::::::
   12.07.      4.02 GB  |  127.69 GB  |  131.71 GB   %::::::::::::::::
   13.07.      4.17 GB  |  134.46 GB  |  138.63 GB   %:::::::::::::::::
   14.07.      4.98 GB  |  167.25 GB  |  172.24 GB   %:::::::::::::::::::::
   15.07.      4.72 GB  |  153.59 GB  |  158.32 GB   %::::::::::::::::::::
   16.07.      4.62 GB  |  148.50 GB  |  153.12 GB   %:::::::::::::::::::
   17.07.      4.78 GB  |  155.97 GB  |  160.75 GB   %::::::::::::::::::::
   18.07.      1.56 GB  |   51.22 GB  |   52.78 GB   :::::::
------------------------+-------------+----------------------------------------
 estimated     4.53 GB  |  148.71 GB  |  153.23 GB

human@ds2-uk:~$ vnstat -m

 eth0  /  monthly

   month         rx      |      tx      |   total
-------------------------+--------------+--------------------------------------
  Jan '09     261.38 GB  |     2.34 TB  |     2.60 TB   %::::::::::::::
  Feb '09     111.07 GB  |     2.97 TB  |     3.08 TB   %::::::::::::::::
  Mar '09     113.04 GB  |     3.22 TB  |     3.33 TB   %::::::::::::::::::
  Apr '09     145.80 GB  |     3.63 TB  |     3.77 TB   %::::::::::::::::::::
  May '09     151.60 GB  |     3.39 TB  |     3.54 TB   %:::::::::::::::::::
  Jun '09     119.16 GB  |     3.69 TB  |     3.80 TB   %:::::::::::::::::::::
  Jul '09      90.43 GB  |     2.59 TB  |     2.68 TB   :::::::::::::::
-------------------------+--------------+--------------------------------------
 estimated    161.73 GB  |     4.63 TB  |     4.78 TB


```

---

### Post by binbash on 2009-07-17
+1 vnstat

---

### Post by Avuton Olrich on 2009-07-23
Oh! vnstat, awesome. Installed and does exactly what I'm looking for. Thanks!!! 

/me watches the counter :popcorn:

---

### Post by philcamlin on 2009-07-24
> **Avuton Olrich said:**
> Oh! vnstat, awesome. Installed and does exactly what I'm looking for. Thanks!!! 

/me watches the counter :popcorn:
you could also use firestarter as a firewall and a bandwidth counter

i just write doen the number befire i shutdown and i add it up at the end of the month

---

