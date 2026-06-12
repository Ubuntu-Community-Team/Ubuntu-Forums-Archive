---
title: "xinepart in kaffeine"
date: 2009-03-04
forum: Multimedia Software
---

### Post by chitowner on 2009-03-04
this is hopefully helpful for others who might be as mystified as i was.

symptom: trying to open a file in kaffeine and getting a failure message about xinepart.

i googled around a bit and hit on something that looked related where a path was suggested: /home/yourdir/.kde/share/apps/kaffeine

here you will find stuff that controls how kaffeine and it's xine component works. first, look into playlists and delete that stuff. it's just a temp list anyway. then back out one level and find the xine.config file. this is most likely the source of your problem.

since the config file is under your home dir you can edit or delete it. what i did was to replace it with a backup copy that was all defaults. deleting it would probably cause kaffeine to replace it the next time you run it, but i didn't test that.

I am aware of another option, but, sorry, can't offer valid advice on it. if you are adventurous you can open kaffeine without trying to load a file, go into settings>xine engine parameters. here you will find tabs for "beginner" and "expert" for various categories; audio, video, media and so forth. NOTE: there is no "reset" option to return these settings to default! BUT if you changed any of these before having problems you can try to change them back.

:rolleyes:

---

