---
title: "[rawstudio] – Unable to compile – SQLITE3 – No package 'sqlite3' found"
date: 2022-07-10
forum: Multimedia Software
---

### Post by acamat-acubens on 2022-07-10
Hi folks,

after downloading the repository and installing all required libraries, autogen.sh runs on Ubuntu 20.04.4 LTS (Focal Fossa) in the message:

```

configure: error: Package requirements (sqlite3) were not met:

No package 'sqlite3' found

```

But SqLite 3.31 is already installed:

```

$sudo apt-get install sqlite3
Abhängigkeitsbaum wird aufgebaut.
Statusinformationen werden eingelesen.... Fertig
sqlite3 ist schon die neueste Version (3.31.1-4ubuntu0.3).
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 9 nicht aktualisiert.

```

What can I do to keep going?

-- 
Best wishes
Carsten

---

### Post by &amp;KyT$0P# on 2022-07-10
Do you have [FONT=Courier New]libsqlite3-dev[/FONT] installed?

---

### Post by acamat-acubens on 2022-07-10
> **halogen2 said:**
> Do you have libsqlite3-dev installed?
Thank you so much :). You put me on the right track. After

```

sudo apt-get install libsqlite3-dev
sudo apt-get install liblensfun-dev
sudo apt-get install liblcms2-dev
sudo apt-get install libgphoto2-dev
sudo apt-get install libexiv2-dev
sudo apt-get install fftw3-dev

```

autogen.sh tells me
```

Now type `make' to compile.

```
:). I’ll finish that tomorrow…

--
Best wishes
Carsten

---

