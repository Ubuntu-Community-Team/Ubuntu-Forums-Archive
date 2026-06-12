---
title: "Easy to use bandwidth monitor?"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by SoylentSteak on 2009-05-25
Can someone recommend a program that will allow me to monitor how much bandwidth I've used, preferably one with a GUI, or simple terminal commands, that's in the Ubuntu repositories? I have an overpriced ISP that also limits bandwidth to 100 gigs per month.

---

### Post by gombadi on 2009-05-25
> 
Can someone recommend a program that will allow me to monitor how much bandwidth I've used, preferably one with a GUI, or simple terminal commands, that's in the Ubuntu repositories


```

sudo apt-get install vnstat

```

It produces output like this

```

human@ds2-uk:~$ vnstat -m

 eth0  /  monthly

   month         rx      |      tx      |   total
-------------------------+--------------+--------------------------------------
  Jan '09     261.38 GB  |     2.34 TB  |     2.60 TB   %::::::::::::::
  Feb '09     111.07 GB  |     2.97 TB  |     3.08 TB   %::::::::::::::::
  Mar '09     113.04 GB  |     3.22 TB  |     3.33 TB   %::::::::::::::::::
  Apr '09     145.80 GB  |     3.63 TB  |     3.77 TB   %:::::::::::::::::::::
  May '09     108.78 GB  |     2.64 TB  |     2.75 TB   %:::::::::::::::
-------------------------+--------------+--------------------------------------
 estimated    132.24 GB  |     3.21 TB  |     3.34 TB
human@ds2-uk:~$ vnstat -d

 eth0  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   27.04.      3.11 GB  |   85.42 GB  |   88.53 GB   :::::::::::::
   28.04.      3.44 GB  |   95.62 GB  |   99.06 GB   %::::::::::::::
   29.04.      3.66 GB  |  105.94 GB  |  109.60 GB   %:::::::::::::::
   30.04.      3.66 GB  |  107.32 GB  |  110.98 GB   %::::::::::::::::
   01.05.      3.35 GB  |   96.78 GB  |  100.13 GB   %::::::::::::::
   02.05.      2.76 GB  |   77.19 GB  |   79.95 GB   ::::::::::::
   03.05.      2.55 GB  |   71.32 GB  |   73.87 GB   :::::::::::
   04.05.      2.69 GB  |   77.86 GB  |   80.55 GB   ::::::::::::
   05.05.      4.53 GB  |  157.12 GB  |  161.64 GB   %::::::::::::::::::::::::
   06.05.      3.90 GB  |  132.31 GB  |  136.21 GB   %::::::::::::::::::::
   07.05.      3.15 GB  |   97.77 GB  |  100.92 GB   :::::::::::::::
   08.05.      3.30 GB  |  104.07 GB  |  107.37 GB   ::::::::::::::::
   09.05.     18.28 GB  |  109.98 GB  |  128.26 GB   %%%::::::::::::::::
   10.05.      3.23 GB  |   92.55 GB  |   95.78 GB   ::::::::::::::
   11.05.      3.16 GB  |   93.87 GB  |   97.03 GB   :::::::::::::::
   12.05.      3.89 GB  |  118.18 GB  |  122.07 GB   %:::::::::::::::::
   13.05.      3.69 GB  |  111.14 GB  |  114.83 GB   %::::::::::::::::
   14.05.      3.79 GB  |  119.72 GB  |  123.52 GB   %::::::::::::::::::
   15.05.      3.80 GB  |  115.00 GB  |  118.80 GB   %:::::::::::::::::
   16.05.      3.34 GB  |   98.86 GB  |  102.20 GB   :::::::::::::::
   17.05.      2.77 GB  |   79.77 GB  |   82.54 GB   ::::::::::::
   18.05.      3.41 GB  |  109.12 GB  |  112.53 GB   %::::::::::::::::
   19.05.      4.12 GB  |  133.83 GB  |  137.95 GB   %::::::::::::::::::::
   20.05.      4.14 GB  |  134.84 GB  |  138.98 GB   %::::::::::::::::::::
   21.05.      3.91 GB  |  121.32 GB  |  125.23 GB   %::::::::::::::::::
   22.05.      3.71 GB  |  115.75 GB  |  119.46 GB   %:::::::::::::::::
   23.05.      2.99 GB  |   89.75 GB  |   92.74 GB   ::::::::::::::
   24.05.      8.59 GB  |   71.24 GB  |   79.83 GB   %:::::::::::
   25.05.      3.53 GB  |  106.21 GB  |  109.74 GB   %:::::::::::::::
   26.05.      2.22 GB  |   70.62 GB  |   72.84 GB   :::::::::::
------------------------+-------------+----------------------------------------
 estimated     4.25 GB  |  135.22 GB  |  139.47 GB


```

or if you want a daily email then make a cronjob with
```

vnstat -m | mail -s "Data usage up to $(date) for $(hostname)" user@domain.com

```

---

### Post by ad_267 on 2009-05-25
+1 for vnstat

After you've installed it you have to set it up with "sudo vnstat -u -i eth0", replacing eth0 with the correct interface.

Then you can run "vnstat" to see your usage, or look at the man page for more options.

If you compile vnstat yourself you can get a vnstati command that produces pretty graphs.

---

