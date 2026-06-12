---
title: "MythTV doesn't  see XMLTV-Grabber anymore!"
date: 2009-02-11
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2009-02-11
Hi, when i add a Video Source in my mythtv-backend-setup, it "searching for xmltv grabber installed" which is installed but it doesn't see it.

This is the output

```

2009-02-12 00:21:27.815 Running tv_find_grabbers.
2009-02-12 00:21:53.110 tv_find_grabbers exited early or we timed out waiting
```


But while i launch tv_find_grabbers in a normal terminal

```
master@master-desktop:~$ tv_find_grabbers 
/usr/local/bin/tv_grab_ar|Argentina
/usr/local/bin/tv_grab_br_net|Brazil (NET)
/usr/local/bin/tv_grab_ch_search|Switzerland (tv.search.ch)
/usr/local/bin/tv_grab_combiner|Combine data from several other grabbers
/usr/local/bin/tv_grab_dk_dr|Denmark
/usr/local/bin/tv_grab_dtv_la|Latin America Direct TV listings
/usr/local/bin/tv_grab_ee|Estonia (www.kava.ee)
/usr/local/bin/tv_grab_es|Spain
/usr/local/bin/tv_grab_es_laguiatv|Spain (laguiatv.com)
/usr/local/bin/tv_grab_es_miguiatv|Spain (miguiatv.com)
/usr/local/bin/tv_grab_eu_epgdata|Parts of Europe (commercial) (www.epgdata.com)
/usr/local/bin/tv_grab_fi|Finland
/usr/local/bin/tv_grab_fr|France
/usr/local/bin/tv_grab_hr|Croatia
/usr/local/bin/tv_grab_huro|Hungary/Romania
/usr/local/bin/tv_grab_it|Italy
/usr/local/bin/tv_grab_na_dd|North America (Data Direct)
/usr/local/bin/tv_grab_na_dtv|North America using www.directv.com
/usr/local/bin/tv_grab_no_gfeed|Norway (beta)
/usr/local/bin/tv_grab_re|Reunion Island
/usr/local/bin/tv_grab_se_swedb|Sweden (tv.swedb.se)
/usr/local/bin/tv_grab_uk_bleb|United Kingdom (bleb.org)
/usr/local/bin/tv_grab_uk_rt|United Kingdown/Republic of Ireland (Radio Times)
/usr/local/bin/tv_grab_za|South Africa
/usr/bin/tv_grab_ar|Argentina
/usr/bin/tv_grab_be|Belgium
/usr/bin/tv_grab_br_net|Brazil (NET)
/usr/bin/tv_grab_ch_search|Switzerland (tv.search.ch)
/usr/bin/tv_grab_combiner|Combine data from several other grabbers
/usr/bin/tv_grab_dk|Denmark
/usr/bin/tv_grab_dtv_la|Latin America Direct TV listings
/usr/bin/tv_grab_ee|Estonia (www.kava.ee)
/usr/bin/tv_grab_es|Spain
/usr/bin/tv_grab_es_laguiatv|Spain (laguiatv.com)
/usr/bin/tv_grab_es_miguiatv|Spain (miguiatv.com)
/usr/bin/tv_grab_eu_epgdata|Parts of Europe (commercial) (www.epgdata.com)
/usr/bin/tv_grab_fi|Finland
/usr/bin/tv_grab_fr|France
/usr/bin/tv_grab_hr|Croatia
/usr/bin/tv_grab_huro|Hungary/Romania
/usr/bin/tv_grab_il|Israel
/usr/bin/tv_grab_it|Italy
/usr/bin/tv_grab_jp|Japan
/usr/bin/tv_grab_na_dd|North America (Data Direct)
/usr/bin/tv_grab_na_dtv|North America using www.directv.com
/usr/bin/tv_grab_no_gfeed|Norway (beta)
/usr/bin/tv_grab_pt|Portugal
/usr/bin/tv_grab_re|Reunion Island
/usr/bin/tv_grab_se_swedb|Sweden (tv.swedb.se)
/usr/bin/tv_grab_uk_bleb|United Kingdom (bleb.org)
/usr/bin/tv_grab_uk_rt|United Kingdom/Republic of Ireland (Radio Times)
/usr/bin/tv_grab_za|South Africa
master@master-desktop:~$ 


```

I really don't understand, can u help me plz??

---

### Post by nickrout on 2009-02-11
xmltv now provides so many grabbers that the script to collect them up doesn't complete before myth times out (30 sec I think).

Delete most of them (obviously not the ones you will want) and try again. The script will then take less than 30 secs (yes I struck this two nights ago!)

---

### Post by impossibilechecisiaquesto on 2009-02-12
Can i kiss you!!!))  :P

By the way, thhhannnkkk yooouuu!

---

### Post by nickrout on 2009-02-12
> **impossibilechecisiaquesto said:**
> Can i kiss you!!!))  :P

By the way, thhhannnkkk yooouuu!

photo first before kisses please :)

I can't claim much kudos, I spent 10 minutes on google to find the answer a couple of nights ago, the person whose post I found deserves the praise :)

---

