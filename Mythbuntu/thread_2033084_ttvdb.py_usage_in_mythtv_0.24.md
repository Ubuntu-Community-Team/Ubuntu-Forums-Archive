---
title: "ttvdb.py usage in mythtv 0.24"
date: 2012-07-25
forum: Mythbuntu
---

### Post by samihs72 on 2012-07-25
Hi!

I am trying to get posters or cover arts to work with Finnish names for American TV-series, example "Law & Order" is in Finnish "Kova laki". But posters are not coming for TV recordings. How I should make those localizations?

I can find those series manually:

```

sami@sami-htpc:/$ ./usr/share/mythtv/metadata/Television/ttvdb.py -l fi -M "Kova laki"
<?xml version='1.0' encoding='UTF-8'?>
<metadata>
  <item>
    <language>fi</language>
    <title>Kova laki</title>
    <inetref>72368</inetref>
    <imdb>0098844</imdb>
    <tmsref>EP00017617</tmsref>
     <description>"In the criminal justice system, the people are  represented by two separate yet equally important groups. The police who  investigate crime and the district attorneys who prosecute the  offenders. These are their stories." Filmed entirely on location in New  York, the realistic program looks at crime and justice from a dual  perspective. In the first half-hour, Detective Cyrus Lupo and his new  partner, Detective Kevin Bernard, investigate crimes and apprehend  suspects under the supervision of their precinct lieutenant, Anita Van  Buren. In the second half-hour, the focus shifts to the criminal courts  as Executive Assistant District Attorney Michael Cutter and the  Assistant District Attorney Connie Rubirosa work within a complicated  justice system to prosecute the accused under the guidance of the newly  appointed District Attorney Jack McCoy.</description>
    <releasedate>1990-09-13</releasedate>
    <images>
       <image type="banner"  url="http://www.thetvdb.com/banners/graphical/72368-g5.jpg"  thumb="http://www.thetvdb.com/banners/_cache/graphical/72368-g5.jpg"/>
    </images>
  </item>
  <item>
    <language>fi</language>
    <title>Kova laki: ErikoisyksikkÃ¶ (K15)</title>
    <inetref>75692</inetref>
    <imdb>0203259</imdb>
    <tmsref>EP00316978</tmsref>
     <description>This hard-hitting and emotional companion series  from NBC's Law &amp; Order franchise chronicles the life and crimes  of the elite Special Victims Unit of the New York Police Department. Law  &amp; Order: Special Victims Unit was created by Emmy Award-winning  producer **** Wolf. SVU celebrated its 200th episode in April 2008. The  drama follows Det. Elliot Stabler, a seasoned veteran of the unit who  has seen it all, and his partner, Olivia Benson, whose difficult past is  the reason she joined the unit.</description>
    <releasedate>1999-09-20</releasedate>
    <images>
       <image type="banner"  url="http://www.thetvdb.com/banners/graphical/75692-g2.jpg"  thumb="http://www.thetvdb.com/banners/_cache/graphical/75692-g2.jpg"/>
    </images>
  </item>
</metadata>

```I have found this instruction page but I cannot follow it completely: [http://www.mythtv.org/wiki/MythTV_Universal_Metadata_Format](http://www.mythtv.org/wiki/MythTV_Universal_Metadata_Format)

---

### Post by samihs72 on 2012-07-29
Hi! Does anyone has idea for getting posters working with non-English TV series names?

---

### Post by nickrout on 2012-08-01
It may depend on whether that programme has a Finnish language entry in thetvdb.com. It doesn't seem to and presumably therefore fails.

---

### Post by samihs72 on 2012-08-01
> **nickrout said:**
> It may depend on whether that programme has a Finnish language entry in thetvdb.com. It doesn't seem to and presumably therefore fails.
Hi nickrout! It has Finnish entry in thetvdb.com and I would like to match that entry to "Law&Order" somehow in mythtv.
[http://thetvdb.com/index.php?tab=series&id=72368&lid=11](http://thetvdb.com/index.php?tab=series&id=72368&lid=11)

---

