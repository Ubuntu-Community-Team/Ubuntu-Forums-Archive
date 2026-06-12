---
title: "Mediatomb not seeing mp4 file"
date: 2010-04-02
forum: Multimedia Software
---

### Post by Zero_Black on 2010-04-02
I'm running mediatomb and I'm trying to add an mp4 file to the database and the scanner doesn't recognise it as a video file. I can't find anything in the documentation about adding other filetypes and I thought mp4s were supposed to be included anyway.

Has anyone else had this issue or am I missing something obvious? I know it's going to be something simple but I can't find the answer I'm looking for. Any help would be much appreciated.

---

### Post by Zero_Black on 2010-04-05
Solved my issue. I realised I hadn't added the mapping from mp4 to video/mp4 in the /etc/mediatomb/config.xml file! So adding this line:
```

<map from="mp4" to="video/mp4"/>
```in between the <extension-mimetype> tags fixed the issue :roll:

---

