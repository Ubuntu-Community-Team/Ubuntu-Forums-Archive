---
title: "does mythexport work in 8.10 ?"
date: 2009-10-12
forum: Mythbuntu
---

### Post by jeremycobert on 2009-10-12
hey guys i just tried to install mythexport following these guidelines 

```
sudo apt-get update
sudo apt-get install mythexport atomicparsley
```

[https://help.ubuntu.com/community/MythExport#Installation](https://help.ubuntu.com/community/MythExport#Installation)

it seems to have installed with out errors, but when i go to
[http://localhost/mythexport/](http://localhost/mythexport/) 
i get "Internal Server Error"

i restarted apache webserver and still get nowhere. also there is no transcoding options for it in the myth frontend.

am i missing a step ?

---

### Post by rhpot1991 on 2009-11-30
> **jeremycobert said:**
> hey guys i just tried to install mythexport following these guidelines 

```
sudo apt-get update
sudo apt-get install mythexport atomicparsley
```

[https://help.ubuntu.com/community/MythExport#Installation](https://help.ubuntu.com/community/MythExport#Installation)

it seems to have installed with out errors, but when i go to
[http://localhost/mythexport/](http://localhost/mythexport/) 
i get "Internal Server Error"

i restarted apache webserver and still get nowhere. also there is no transcoding options for it in the myth frontend.

am i missing a step ?

Check your /var/log/apache2/error.log to see what is going wrong.

---

