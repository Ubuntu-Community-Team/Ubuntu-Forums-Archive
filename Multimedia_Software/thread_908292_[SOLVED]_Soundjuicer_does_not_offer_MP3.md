---
title: "[SOLVED] Soundjuicer does not offer MP3"
date: 2008-09-02
forum: Multimedia Software
---

### Post by johann_p on 2008-09-02
In the preferences, Soundjuicer does not offer MP3 as a possible output format. However, Edit Profiles ... does show a "CD Quality, MP3" profile. This profile is not available in the selection menu for "Output Format" though.

Why? And how can I make Soundjuicer produce MP3 output?

---

### Post by johann_p on 2008-09-02
I figured out that it needs these additional packages installed:

lame gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 

Beats me why they are not installed by default if they are needed for such basic functionality.

---

### Post by kpkeerthi on 2008-09-02
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)
[http://www.ubuntu.com/community/ubuntustory/licensing](http://www.ubuntu.com/community/ubuntustory/licensing)

---

