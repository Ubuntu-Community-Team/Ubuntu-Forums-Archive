---
title: "MythZoneminder Issues"
date: 2010-02-03
forum: Mythbuntu
---

### Post by Binface on 2010-02-03
Hi all.

Been banging my head against these issues for a while. I've searched everything and everywhere I could for a solution, but it seems my problems are pretty unique. Here's the run down of my situation.

I'm using Ubuntu 9.10 on a box that will handle CCTV (I realise it's not mythbuntu, but I felt this forum was appropriate before I raise bug reports). I've got Zoneminder 1.24.1 working with little trouble, and everything is working as it should be.

However I wasn't happy with how it looked, so I decided to give mythtv + mythzoneminder a go.

That installed fine with little trouble aswell. By little trouble I just mean the usual inexperienced linux user problems.

Now it all works fine EXCEPT the following issues:

[LIST]
[*]When watching the live feed through mythzoneminder, most of the colours are wrong. By that I mean reds are green, blues are reds. It's not inversed, just not interpreting the colours right. However when monitoring zoneminder in the usual fashion, it's fine there
[*]The events do not play very well at all. When watching events, (funnily enough the colours are right here) the mythzoneminder event shows only a fraction of the actual event, and always hangs on the 2nd to last frame for the best part of 10seconds.
[*]Icons in the events viewer where you chose what event you wish to watch only show green.
[*]Text formatting is a bit off
[/LIST]
I don't have any of these issues when using just the normal Zoneminder console, but I would prefer mythzoneminder just so I can eventually use this box as a CCTV viewer and an HTPC for TV viewing/recording. Which means browsing through events on my couch using a remote :D

I'm wondering whether its because I'm using versions of ubuntu or zoneminder that are too new. Does it only support older versions of zoneminder?

Thanks in advance,
Kayne

Edit: Oops forgot to add I'm using mythzoneminder 0.22 and mythtv 0.22 stable. I assume it's all up to date as I used apt-get

---

### Post by mgc8 on 2010-02-05
I'm running Myth+ZM under Debian with the latest packages, and I am seeing the same issue with wrong (green/pink) colours... I think the problem lies with mythzmserver, however I didn't have the time to troubleshoot it.

Bottom line, this is not an Ubuntu problem, I think the bug should be opened upstream. About the rest or the problems, couldn't say since I don't use that functionality...

---

### Post by dluzin on 2010-03-15
I've solved it by changing the order of r,g and b in /mythplugins/mythzoneminder/mythzoneminder/zmliveplayer.cpp:

445	    else
446	    {
447	        // all other color palettes
448	        for (pos_data = 0; pos_data < (unsigned int) (m_monitor.width * m_monitor.height * 3); )
449	        {
450	            r = buffer[pos_data++];
451	            g = buffer[pos_data++];
452	            b = buffer[pos_data++];
453	            [COLOR="Red"]m_rgba[pos_rgba++] = b;[/COLOR]
454	            [COLOR="red"]m_rgba[pos_rgba++] = g;[/COLOR]
455	            [COLOR="red"]m_rgba[pos_rgba++] = r;[/COLOR]
456	            m_rgba[pos_rgba++] = 0xff;
457	        }

Should be:

[B]453	            m_rgba[pos_rgba++] = g;
454	            m_rgba[pos_rgba++] = r;
455	            m_rgba[pos_rgba++] = b;[/B]

---

### Post by summetj on 2010-07-31
I'm having the same problems with a mythbuntu distribution. Has this problem/fix been reported to the MythTv (Mythzoneminder plugin) developers so that a fix will eventually be packaged?

Jay

---

### Post by Gibby13 on 2010-08-15
> **dluzin said:**
> I've solved it by changing the order of r,g and b in /mythplugins/mythzoneminder/mythzoneminder/zmliveplayer.cpp:

445        else
446        {
447            // all other color palettes
448            for (pos_data = 0; pos_data < (unsigned int) (m_monitor.width * m_monitor.height * 3); )
449            {
450                r = buffer[pos_data++];
451                g = buffer[pos_data++];
452                b = buffer[pos_data++];
453                [COLOR=Red]m_rgba[pos_rgba++] = b;[/COLOR]
454                [COLOR=red]m_rgba[pos_rgba++] = g;[/COLOR]
455                [COLOR=red]m_rgba[pos_rgba++] = r;[/COLOR]
456                m_rgba[pos_rgba++] = 0xff;
457            }

Should be:

[B]453                m_rgba[pos_rgba++] = g;
454                m_rgba[pos_rgba++] = r;
455                m_rgba[pos_rgba++] = b;[/B]

I can't find that file anywhere. I installed mythzoneminder from the package manager and got it all working except the green haze issue.

---

### Post by summetj on 2010-08-16
> **Gibby13 said:**
> I can't find that file anywhere. I installed mythzoneminder from the package manager and got it all working except the green haze issue.

The .cpp file is found in the source code distribution for MythTV (the mythplugins package specifically...I downloaded the 0.23 fixes package, compiled it after making the changes, (and having to move a lot of include files around, link to libraries in the correct location, etc..) and re-compiled the mythzoneminder.so plugin file, which fixed my problem.
Jay

---

### Post by Gibby13 on 2010-08-23
Any steps to do that? I have tried for a few days worked through some issues trying to compile but still no luck.

---

### Post by summetj on 2010-08-24
It's not an easy process, and I don't recommend it. (Hence my asking to ensure that this fix gets rolled into upstream so it will automatically just work on the next distribution...)

Basically, MythBuntu compiles MythTV and it's plugins with the includes and libraries in a different directory from the default used by the "stock" MythTV packages. So when you try and edit the code and re-compile the mythzoneminder plugin from the stock code, you have to change the include/lib directories.

So, you either have to set up ALL of the include and lib directories correctly in the configure script, or copy all of the .H files that you need into your build directory for the plugin, and symlink all of the libraries to the correct directory.  (The 2nd way is NOT THE RIGHT WAY, but it worked for me when the first way didn't...)
Jay

---

### Post by Gibby13 on 2010-08-24
I updated my mythzoneminder from the repo today and well it broke.... Says "The plugin mythzoneminder has failed to run for some reason..." That is not much help, I did check to make sure mythzmserver is running

---

### Post by Gibby13 on 2010-08-24
Got it fixed, but still have the color issues..... It has been almost 6 months..... so the fix has not been packaged yet :(

---

