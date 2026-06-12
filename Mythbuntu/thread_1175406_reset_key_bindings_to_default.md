---
title: "reset key bindings to default"
date: 2009-06-01
forum: Mythbuntu
---

### Post by smgerlich on 2009-06-01
Is there any way to reset the key bindings to the default? I'm a complete noob, and, as usual, I've done something a little stupid. I changed some of the key bindings without knowing what I was doing, and now there are no bindings for select and a few other important commands within the front-end. Thus, I can't change the bindings back to normal in the front-end because I can't select anything or bring up the menu to make changes. 

I was hoping that there was either a way to just reset the bindings to the default, or to change the bindings manually, outside the gui. 

Any help is appreciated!

---

### Post by joho500 on 2009-06-02
You can change them back in Mythweb. That way you don't need the frontend.

Cheers,
Joost

---

### Post by smgerlich on 2009-06-04
Thanks Joost, I actually got frustrated and did a clean reformat and re-install of Mythbuntu before seeing your response, but now I know where I can change things in the future. :)

---

### Post by medley_44 on 2010-08-01
From: [http://www.mythtv.org/docs/mythtv-HOWTO-14.html](http://www.mythtv.org/docs/mythtv-HOWTO-14.html)

```

echo "delete from keybindings ;" | mysql -u mythtv -p<pass> mythconverg

```

Replace <pass> with your database password, which can be found in ~/.mythtv/mysql.txt

---

