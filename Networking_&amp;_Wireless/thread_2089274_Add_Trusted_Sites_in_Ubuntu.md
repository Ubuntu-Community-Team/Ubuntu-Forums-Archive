---
title: "Add Trusted Sites in Ubuntu"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by GreenRaccoon on 2012-11-28
Ubuntu 12.04 LTS Precise Pangolin 64-bit

Is there a way to add trusted sites in Ubuntu? I know how to do it in Windows, but not in Ubuntu. On Windows, it says, "Add trusted site to the zone." I couldn't find an option for this under any of the Network Settings in Ubuntu.

I don't really want to boot into Windows whenever I have to go to this one site.

---

### Post by haqking on 2012-11-28
> **GreenRaccoon said:**
> Ubuntu 12.04 LTS Precise Pangolin 64-bit

Is there a way to add trusted sites in Ubuntu? I know how to do it in Windows, but not in Ubuntu. On Windows, it says, "Add trusted site to the zone." I couldn't find an option for this under any of the Network Settings in Ubuntu.

I don't really want to boot into Windows whenever I have to go to this one site.

You are referring to Internet Explorer and not Windows the OS.

So it is a browser thing, depends what browser you are using in Linux.

If it is Firefox for example then you can do something like this:

Use address bar and type ```
about:config
```then scroll to the line that says **network.automatic-ntlm-auth.trusted-uris**. 

Double clicking this line will pop up a string entry

Then enter the URI to suit such as the following:

ubuntuforums.org, askubuntu.com

etc using commas between each URI

also i suggest using NoScript and other extensions to configure what happens on all sites

I suggest reading the [Basic Security Wiki  ]("https://wiki.ubuntu.com/BasicSecurity")where there is a section and links on how to configure your browser and add-ons such as NoScript.

Peace

---

