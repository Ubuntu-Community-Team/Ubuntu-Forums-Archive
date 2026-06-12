---
title: "No visual effects in karmic 9.10; &quot;extra&quot; in 9.04"
date: 2010-03-22
forum: Multimedia Software
---

### Post by antodasana on 2010-03-22
Hello.

- HP Pavilion dv2000
- 9.10 just installed (not updated from 9.04) and updated
- kernel 2.6.31-20-generic
- direct rendering: Yes
- Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

I can't use any visual effect but I was using "Extra" visual effects with 9.04, same laptop.

How is that possible? How can I enjoy visual effects again?

Thanks.
Antonio.

---

### Post by Yellow Pasque on 2010-03-22
Can you post the output of these commands?:
```
LIBGL_DEBUG=verbose glxinfo
compiz --replace
```

---

### Post by antodasana on 2010-03-23
Fixed just removing xorg.conf.

Details here:

[https://answers.launchpad.net/ubuntu/+question/105202](https://answers.launchpad.net/ubuntu/+question/105202)

Thank you very much.

---

### Post by barrymajbj on 2011-01-11
> **antodasana said:**
> Hello.- HP Pavilion dv2000- 9.10 just installed (not updated from 9.04) and updated- kernel 2.6.31-20-generic- direct rendering: Yes- Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics [[COLOR=#000000]Controller[/COLOR]](http://www.salmonit.net/ko/pets/dog-diet-raw-food.html) (rev 03)I can't use any visual effect but I was using "Extra" visual effects with 9.04, same laptop.How is that possible? How can I enjoy visual effects again?Thanks.Antonio.Now I have a more clear idea about it, I'm new to this.

---

