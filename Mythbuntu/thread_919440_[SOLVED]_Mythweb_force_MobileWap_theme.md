---
title: "[SOLVED] Mythweb: force Mobile/Wap theme"
date: 2008-09-14
forum: Mythbuntu
---

### Post by pssturges on 2008-09-14
I'm want to be able view mythweb on my iphone using the wap theme but the iphone safari browser is not recognised as a mobile device. Is there any way I can force it? 

Cheers
Phil

---

### Post by anonymousdog on 2008-09-14
"iPhone" is right in the user agent string for the iPhone; so, it should be pretty easy to edit /usr/share/mythtv/mythweb/includes/mobile.php to include an entry for the iPhone that sets screen size to 480x320.

---

### Post by pssturges on 2008-09-15
Yep, That did it! Thanks

---

### Post by SteveGodfrey on 2008-10-17
Can you post the line(s) you added to mobile.php?

I'm trying to do the same.

Thanks

---

### Post by grytpype on 2008-10-18
Add the following line

'iPhone' => array('width' => 320, 'height' => 480),

before

/* Phones using the Series 60 platform, e.g. Nokia 3650 and 6600. */




This works to get Mythweb to recognize the iPhone as a mobile phone, but the height and width are still screwed up, see attached photo.

If someone knows of a fix for that pls advise.

---

### Post by macjones on 2010-02-19
For Android....

[PHP]    */
    $mobiles = array(
                
                 'Android'  => array('width' => 320, 'height' => 480),

[/PHP]

Your resolution may differ...

---

### Post by geekyhawkes on 2010-02-21
Anyone know how Opera on a HD2 would show up or how i can find out?  This is a great little tweak if i can get it working!

solved :  HTC_HD2_T8585

---

### Post by dannyboy79 on 2010-04-08
> **grytpype said:**
> Add the following line

'iPhone' => array('width' => 320, 'height' => 480),

before

/* Phones using the Series 60 platform, e.g. Nokia 3650 and 6600. */




This works to get Mythweb to recognize the iPhone as a mobile phone, but the height and width are still screwed up, see attached photo.

If someone knows of a fix for that pls advise.
looking for a fix for this also

---

### Post by SiHa on 2010-04-09
> **geekyhawkes said:**
> 
solved :  HTC_HD2_T8585

Care to share where you got that little snippet from? I'm eagerly awaiting delivery of an HTC Desire, and would really like to have Mythweb on it.

---

### Post by dannyboy79 on 2010-04-20
bump, ne1 else trying to get a better readable UI for mythweb viewing on the iphone? please post how you did it.

---

### Post by geekyhawkes on 2010-04-20
> Care to share where you got that little snippet from? I'm eagerly awaiting delivery of an HTC Desire, and would really like to have Mythweb on it.

The user agent from WM can be found in this registry tag;

HLKM/Software/Opera/Prefs/User Prefs/Custom User-Agent 

Hope this helps.

---

