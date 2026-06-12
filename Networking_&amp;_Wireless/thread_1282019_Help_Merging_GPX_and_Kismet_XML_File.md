---
title: "Help Merging GPX and Kismet XML File"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by s3MA00RRNY on 2009-10-03
I'm not sure if this is the best place to ask this.

I want to take the data from a GPX file and merge it with a Kismet XML.

Sample of Kismet XML:

```
  <wireless-network number="119" type="infrastructure" wep="false" cloaked="false" first-time="Sat Oct  3 19:03:06 2009" last-time="Sat Oct  3 19:03:43 2009">
    <SSID>home603</SSID>
    <BSSID>00:1A:70:EE:D4:F9</BSSID>
    <channel>6</channel>
    <maxrate>54.0</maxrate>
    <maxseenrate>1000</maxseenrate>
    <encoding>802.11n 20MHz</encoding>
    <encryption>None</encryption>
    <packets>
      <LLC>2</LLC>
      <data>0</data>
      <crypt>0</crypt>
      <weak>0</weak>
      <dupeiv>0</dupeiv>
      <total>2</total>
    </packets>
    <datasize>0</datasize>
    <gps-info unit="english">
      <min-lat>90.000000</min-lat>
      <min-lon>180.000000</min-lon>
      <min-alt>0.000000</min-alt>
      <min-spd>0.000000</min-spd>
      <max-lat>-90.000000</max-lat>
      <max-lon>-180.000000</max-lon>
      <max-alt>0.000000</max-alt>
      <max-spd>0.000000</max-spd>
    </gps-info>
  </wireless-network>
</detection-run>

```Sample of GPX:

```
<gpx version="1.0" creator="ExpertGPS 1.1 - http://www.topografix.com" xsi:schemaLocation="http://www.topografix.com/GPX/1/0 http://www.topografix.com/GPX/1/0/gpx.xsd">
<time>2002-02-27T17:18:33Z</time>
<bounds minlat="42.401051" minlon="-71.126602" maxlat="42.468655" maxlon="-71.102973"/>
<wpt lat="42.438878" lon="-71.119277">
<ele>44.586548</ele>
<time>2001-11-28T21:05:28Z</time>
<name>5066</name>
<desc>5066</desc>
<sym>Crossing</sym>
<type>Crossing</type>
</wpt>
```

Basically, take the "first-time" of the Kismet file and compare it with time in the GPX file. If they match, change min-lat and max-lat in the Kismet to the lat value in the GPX and take the min-lon and max-lon and change it to the lon. Then write the new KisML back to a file.

---

### Post by s3MA00RRNY on 2009-10-04
bump.

---

### Post by s3MA00RRNY on 2009-10-08
bump.

---

### Post by s3MA00RRNY on 2009-10-10
bump.

---

### Post by s3MA00RRNY on 2009-10-12
bump.

---

### Post by s3MA00RRNY on 2009-10-29
bump.

---

### Post by s3MA00RRNY on 2009-11-06
bump.

---

### Post by s3MA00RRNY on 2010-03-19
I made my own solution. [http://ubuntuforums.org/showthread.php?t=1386660](http://ubuntuforums.org/showthread.php?t=1386660)

---

