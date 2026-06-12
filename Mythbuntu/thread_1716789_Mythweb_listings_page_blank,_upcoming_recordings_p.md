---
title: "Mythweb listings page blank, upcoming recordings page broken - segmentation faults"
date: 2011-03-29
forum: Mythbuntu
---

### Post by bgood on 2011-03-29
This has been going on for months now, I was hoping it would be fixed in an update but alas nothing and I've done a load of googling but not got anywhere with it so decided to ask for help here.

The main mythweb page works fine but the listings page doesn't show any content, the background is all present as are the options across the top but the main section where the listings should be is just blank.

The recording schedules and upcoming recordings pages don't work at all I just get a 'web page is not available error'

Searches brings up a list of the pre-defined search options which all seem to work except 'Films' which just gives a page full of these errors
```
Warning at /usr/share/mythtv/mythweb/includes/css.php, line 24:
!!NoTrans: Cannot use a scalar value as an array!!

Warning at /usr/share/mythtv/mythweb/modules/tv/includes/programs.php, line 192:
!!NoTrans: Attempt to modify property of non-object!!
```

Whenever I try and access either the listings page, recording schedules or the upcoming recordings page I get this in the apache2 error.log
```
[Tue Mar 29 04:56:09 2011] [notice] child pid 15120 exit signal Segmentation fault (11)

```

I have zero knowledge of php and am really at a loss as to what to do so any help/suggestions would be greatly appreciated, thx.

---

### Post by bgood on 2011-03-29
Sorry, just to add, I'm using 0.24 (v0.24-222-g1f532a5) and mythfill listings and the guide in the frontend are working fine.

---

### Post by gmaltby on 2012-04-11
I have the same issue.

I've found that ticking 'genre_colours' (Mythweb -> Settings -> MythWeb ->MythWeb Defaults), bypasses the code causing the problem.

Specifically,
```
    // Disable categories colorization
        if (isset($_SESSION['genre_colors'])
                  && $_SESSION['genre_colors'] == 0) {
[COLOR="Red"]ERROR[/COLOR] ->    $css_class[] = $cache[$category] = 'cat_Unknown';
            return $css_class[0];
```

---

### Post by GoofysNewquay on 2012-12-22
just encountered the same problem - fix still works - 2012-12-22

---

### Post by Tim_Brown on 2013-08-09
Just encountered this same problem and ticking 'genre_colours' still works!

mythtv (2:0.25.2+fixes.20120802.46cab93-0ubuntu1) on Ubuntu 12.04 LTS

---

