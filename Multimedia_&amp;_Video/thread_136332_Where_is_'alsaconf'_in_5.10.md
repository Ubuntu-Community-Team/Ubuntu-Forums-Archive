---
title: "Where is 'alsaconf' in 5.10?"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by Canellas on 2006-02-25
Hi,

I could not find 'alsaconf' in 5.10. 

If I type 'alsaconf', I get a "bash: alsaconf: command not found", and it does not appear in the list of provided files in 'alsa-utils' package.

Does anyone know how can I get it already compiled? I am having a lot o trouble trying to compile version 1.0.9 from ALSA project site.

Thanks a lot,
  Canellas

---

### Post by Xian on 2006-02-25
The 'alsaconf' function is absent from 5.10 and I know of no method other than compilation to get it included, unless you feel like you would prefer to try installing a Debian alsa-utils package (which could cause even more problems). What is giving you headaches when you compile the application?

---

### Post by Canellas on 2006-02-26
Xian,

During 'make', I get  this error:

Making all in alsaconf
make[1]: Entrando no diretório `/home/apolo/alsa/alsa-utils-1.0.9a/alsaconf'
Making all in po
make[2]: Entrando no diretório `/home/apolo/alsa/alsa-utils-1.0.9a/alsaconf/po'
mv: impossível fazer stat em `t-ja.gmo': Arquivo ou diretório não encontrado
make[2]: ** [ja.gmo] Erro 1
make[2]: Saindo do diretório `/home/apolo/alsa/alsa-utils-1.0.9a/alsaconf/po'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/apolo/alsa/alsa-utils-1.0.9a/alsaconf'
make: ** [all-recursive] Erro 1


The sentence "Entrando no diretório" means "Entering directory",  "impossível fazer" means "impossible to make",  "Saindo do diretório" means "Leaving directory", and "Erro" means (quite obviously) "Error".

So, there is no "t-ja.gmo" file in the "/home/apolo/alsa/alsa-utils-1.0.9a/alsaconf/po" directory, which has only these files:
"
apolo@kent:~/alsa/alsa-utils-1.0.9a$ l alsaconf/po/
total 20
-rw-r--r--  1 apolo apolo 11221 2004-12-29 14:10 ja.po
-rw-r--r--  1 apolo apolo  1889 2006-02-26 15:05 Makefile
-rw-r--r--  1 apolo apolo  1944 2005-01-13 13:32 Makefile.in
"

Should I download an older version of 'alsa-utils'?


Thanks,
  Canellas

---

### Post by Canellas on 2006-02-26
Just to let you know, I tried 'alsa-utils' 1.0.9 and 1.08, and the same mistake ocurred.

---

