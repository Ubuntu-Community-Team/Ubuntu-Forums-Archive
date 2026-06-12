---
title: "TIP: Mythstream &amp; Ubuntu Edgy (6.10)"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by rbm0307 on 2007-03-15
I have installed MythTV under Ubuntu 6.10 (Edgy) recently and attempted to get mythstream working.  I met with some success with the package right "out of the box".  The harvester and play functionality worked except that sound would not work at all.  My PC is equipped with an S/PDIF out which I use to feed digital sound to my receiver.  I also modified the /etc/asound.conf file to pipe audio to both the analogue and digital outputs.  I followed advice given in other forums to modify the mplayer command line to include the flags "-ao oss -vo xv" to get sound and video working in MythTV on other functions such as Play Video and Play Music.  

I managed to get Mythstream to function properly also by supplying these same flags to the mplayer command that Mythstream launches.

To accomplish this, modify the libs/player.xml file in the Mythstream distribution.  Under the <player> stanza, <custom> sub-stanza, replace:

```

      <item>
          <name>-vo</name>
          <value>gl2</value>
      </item>

```
with:
```

      <item>
          <name>-vo</name>
          <value>xv</value>
      </item>
      <item>
          <name>-ao</name>
          <value>oss</value>
      </item>

```

Hope this helps others who might have the same problem as I.

- Robert.

---

### Post by majoridiot on 2007-03-16
great tip and  thanks for sharing! :D

---

### Post by amoore on 2007-06-13
> **rbm0307 said:**
> I have installed MythTV under Ubuntu 6.10 (Edgy) recently and attempted to get mythstream working.  I met with some success with the package right "out of the box".  The harvester and play functionality worked except that sound would not work at all.  My PC is equipped with an S/PDIF out which I use to feed digital sound to my receiver.  I also modified the /etc/asound.conf file to pipe audio to both the analogue and digital outputs.  I followed advice given in other forums to modify the mplayer command line to include the flags "-ao oss -vo xv" to get sound and video working in MythTV on other functions such as Play Video and Play Music.  

I managed to get Mythstream to function properly also by supplying these same flags to the mplayer command that Mythstream launches.

To accomplish this, modify the libs/player.xml file in the Mythstream distribution.  Under the <player> stanza, <custom> sub-stanza, replace:

```

      <item>
          <name>-vo</name>
          <value>gl2</value>
      </item>

```
with:
```

      <item>
          <name>-vo</name>
          <value>xv</value>
      </item>
      <item>
          <name>-ao</name>
          <value>oss</value>
      </item>

```

Hope this helps others who might have the same problem as I.

- Robert.

Could you tell how you got mythstream installed?

---

### Post by SeanOB on 2007-06-21
I'm also interested in installing mythstream and have been looking for a howto with feisty and mythtv 0.20-svn20070122.

Is there a howto somewhere?

-SeanOB

---

