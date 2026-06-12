---
title: "how do i run cgoban?"
date: 2022-10-20
forum: Multimedia Software
---

### Post by phillip1882 on 2022-10-20
so i installed the latest version of java, downloaded the cgoban jar file from gokgs, ran the required command line, but whats the next step? how do i run cgoban?

---

### Post by QIII on 2022-10-20
What "required command line" did you run?  Exact text, please.

---

### Post by phillip1882 on 2022-10-20
java -jar cgoban.jar

---

### Post by QIII on 2022-10-20
And what was the result?

---

### Post by phillip1882 on 2022-10-20
i see a command prompt of
CGoban version 3.5.144-g20af6ff

---

### Post by phillip1882 on 2022-10-20
here's everything i've tried so far
```
phillip1882@phillip1882-spn:~/Desktop$ cd
phillip1882@phillip1882-spn:~$ cd gokgs
phillip1882@phillip1882-spn:~/gokgs$ java -jar cgoban.jar
CGoban version 3.5.144-g20af6ff
phillip1882@phillip1882-spn:~/gokgs$ ./Cgoban
bash: ./Cgoban: No such file or directory
phillip1882@phillip1882-spn:~/gokgs$ ./CGoban
bash: ./CGoban: No such file or directory
phillip1882@phillip1882-spn:~/gokgs$ chmod a+x CGoban
chmod: cannot access 'CGoban': No such file or directory
phillip1882@phillip1882-spn:~/gokgs$ ls
build-data.properties  com     io     META-INF  okhttp3  org
cgoban.jar             dagger  javax  noisy     okio     yoshikawa
phillip1882@phillip1882-spn:~/gokgs$ ./cgoban.jar
bash: ./cgoban.jar: cannot execute binary file: Exec format error
phillip1882@phillip1882-spn:~/gokgs$ chmod a+x cgoban.jar
phillip1882@phillip1882-spn:~/gokgs$
```

---

