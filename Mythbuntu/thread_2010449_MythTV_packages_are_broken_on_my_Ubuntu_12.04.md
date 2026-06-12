---
title: "MythTV packages are broken on my Ubuntu 12.04"
date: 2012-06-25
forum: Mythbuntu
---

### Post by perevera on 2012-06-25
I was using MythTV 0.25 from the latest upgrade of my Ubuntu system to 12.04 version.

This is a barebone ASRock ION 330 (64 bits) that I am using since a while with MythTV.

I suspected of a bug (later on I discovered it was a configuration problem) so in order to get the latest patches I added the Mythbuntu repository (ppa:mythbuntu/0.25) and proceeded to upgrade, but something went wrong:

[I]Preconfigurando paquetes ...
Fallo al preconfigurar mythtv-common, con el código de salida 128
Fallo al preconfigurar mythweb, con el código de salida 128
Fallo al preconfigurar mythtv-database, con el código de salida 128
[/I]

I have tried several things after that, like getting rid of the mythbuntu repositories and trying to re-install what it was packaged with Ubuntu 12.04, but the error above is permanent, even after I purge all MythTV packages.

When I compile/install MythTV from sources, everything works like a charm.

---

### Post by superm1 on 2012-06-25
Is there anything more informative about what's failing in your upgrade logs?

There is generally something higher up.  Provide a full transcript if possible.

If nothing stands out what you should do is modify the postinstall script of those packages failing to add a 'set -x' on the third line.  The scripts are in /var/lib/dpkg/info.  Basically mythtv-database.postinst, etc.  

Run ```
apt-get -f install
``` or ```
dpkg --configure
``` and it should fail again with more information and a big log.

---

### Post by perevera on 2012-06-26
Okey, this all what you can see in dpkg.log when I try to install 'mythtv' after purging:

[I]2012-06-26 19:51:42 startup archives unpack
2012-06-26 19:51:43 upgrade libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 2:0.25.0+fixes.20120622.73bc4
5e-0ubuntu0mythbuntu4
2012-06-26 19:51:43 status half-configured libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:43 status unpacked libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:44 status half-installed libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:45 status half-installed libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:45 status unpacked libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:45 status unpacked libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 install libmythtv-perl <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 status half-installed libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 status unpacked libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 status unpacked libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:47 install mythtv-common <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:47 status half-installed mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 install mythtv-database <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 status half-installed mythtv-database 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 status unpacked mythtv-database 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 status unpacked mythtv-database 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 install mythtv-frontend <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 status half-installed mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:51 status triggers-pending bamfdaemon 0.2.118-0ubuntu0.1
2012-06-26 19:51:51 status half-installed mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:51 status triggers-pending desktop-file-utils 0.20-0ubuntu2
2012-06-26 19:51:51 status half-installed mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:51 status triggers-pending gnome-menus 3.4.0-0ubuntu1
perevera@minipc:/var/log$ cat dpkg.log
2012-06-26 19:51:42 startup archives unpack
2012-06-26 19:51:43 upgrade libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:43 status half-configured libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:43 status unpacked libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:44 status half-installed libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:45 status half-installed libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1
2012-06-26 19:51:45 status unpacked libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:45 status unpacked libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 install libmythtv-perl <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 status half-installed libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 status unpacked libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:46 status unpacked libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:47 install mythtv-common <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:47 status half-installed mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 install mythtv-database <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:49 status half-installed mythtv-database 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 status unpacked mythtv-database 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 status unpacked mythtv-database 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 install mythtv-frontend <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:50 status half-installed mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:51 status triggers-pending bamfdaemon 0.2.118-0ubuntu0.1
2012-06-26 19:51:51 status half-installed mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:51 status triggers-pending desktop-file-utils 0.20-0ubuntu2
2012-06-26 19:51:51 status half-installed mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:51 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2012-06-26 19:51:51 status half-installed mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:52 status unpacked mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:52 status unpacked mythtv-frontend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:52 install mythtv-transcode-utils <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:52 status half-installed mythtv-transcode-utils 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:52 status unpacked mythtv-transcode-utils 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:52 status unpacked mythtv-transcode-utils 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:53 install mythtv-backend <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:53 status half-installed mythtv-backend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:53 status half-installed mythtv-backend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:53 status half-installed mythtv-backend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:53 status half-installed mythtv-backend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:53 status triggers-pending ureadahead 0.100.0-12
2012-06-26 19:51:54 status half-installed mythtv-backend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:54 status triggers-pending ureadahead 0.100.0-12
2012-06-26 19:51:54 status unpacked mythtv-backend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:54 status unpacked mythtv-backend 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:54 install mythtv <ninguna> 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:54 status half-installed mythtv 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:55 status unpacked mythtv 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:55 status unpacked mythtv 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:55 trigproc bamfdaemon 0.2.118-0ubuntu0.1 0.2.118-0ubuntu0.1
2012-06-26 19:51:55 status half-configured bamfdaemon 0.2.118-0ubuntu0.1
2012-06-26 19:51:55 status installed bamfdaemon 0.2.118-0ubuntu0.1
2012-06-26 19:51:55 trigproc desktop-file-utils 0.20-0ubuntu2 0.20-0ubuntu2
2012-06-26 19:51:55 status half-configured desktop-file-utils 0.20-0ubuntu2
2012-06-26 19:51:56 status installed desktop-file-utils 0.20-0ubuntu2
2012-06-26 19:51:56 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2012-06-26 19:51:56 status half-configured gnome-menus 3.4.0-0ubuntu1
2012-06-26 19:51:56 status installed gnome-menus 3.4.0-0ubuntu1
2012-06-26 19:51:56 trigproc ureadahead 0.100.0-12 0.100.0-12
2012-06-26 19:51:56 status half-configured ureadahead 0.100.0-12
2012-06-26 19:51:56 status installed ureadahead 0.100.0-12
2012-06-26 19:51:57 startup packages configure
2012-06-26 19:51:57 configure libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4 <ninguna>
2012-06-26 19:51:57 status unpacked libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:57 status half-configured libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:57 status installed libmyth-0.25-0 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:57 status triggers-pending libc-bin 2.15-0ubuntu10
2012-06-26 19:51:57 configure libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4 <ninguna>
2012-06-26 19:51:57 status unpacked libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:58 status half-configured libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:58 status installed libmythtv-perl 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:58 configure mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4 <ninguna>
2012-06-26 19:51:58 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:58 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:58 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:58 status unpacked mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:58 status half-configured mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4
2012-06-26 19:51:59 trigproc libc-bin 2.15-0ubuntu10 <ninguna>
2012-06-26 19:51:59 status half-configured libc-bin 2.15-0ubuntu10
2012-06-26 19:52:00 status installed libc-bin 2.15-0ubuntu10[/I]

Then if I launch 'sudo dpkg --configure mythtv' it gives the log:
[I]
2012-06-26 19:59:46 startup packages configure
2012-06-26 19:59:46 configure mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4 <ninguna>
2012-06-26 19:59:46 status half-configured mythtv-common 2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4[/I]

I cannot find any clue of what is going wrong out of these logs...

Thanks for helping!

---

### Post by superm1 on 2012-06-27
So the log you are looking for is /var/log/apt/term.log actually.  It should show some more information about exact failures.

---

### Post by perevera on 2012-06-28
> **superm1 said:**
> So the log you are looking for is /var/log/apt/term.log actually.  It should show some more information about exact failures.

I copy that log herebelow.

The only point I understand is configuration of 'mythtv-common' fails. Why?... No idea.

[I]Log started: 2012-06-26  19:51:42
(Leyendo la base de datos ... 224242 ficheros o directorios instalados actualmente.)
Preparando para reemplazar libmyth-0.25-0 2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 (usando .../libmyth-0.25-0_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_amd64.deb) ...
Desempaquetando el reemplazo de libmyth-0.25-0 ...
Seleccionando paquete libmythtv-perl previamente no seleccionado
Desempaquetando libmythtv-perl (de .../libmythtv-perl_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_all.deb) ...
Seleccionando paquete mythtv-common previamente no seleccionado
Desempaquetando mythtv-common (de .../mythtv-common_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_amd64.deb) ...
Seleccionando paquete mythtv-database previamente no seleccionado
Desempaquetando mythtv-database (de .../mythtv-database_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_all.deb) ...
Seleccionando paquete mythtv-frontend previamente no seleccionado
Desempaquetando mythtv-frontend (de .../mythtv-frontend_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_amd64.deb) ...
Seleccionando paquete mythtv-transcode-utils previamente no seleccionado
Desempaquetando mythtv-transcode-utils (de .../mythtv-transcode-utils_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_amd64.deb) ...
Seleccionando paquete mythtv-backend previamente no seleccionado
Desempaquetando mythtv-backend (de .../mythtv-backend_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_amd64.deb) ...
Seleccionando paquete mythtv previamente no seleccionado
Desempaquetando mythtv (de .../mythtv_2%3a0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4_all.deb) ...
Procesando disparadores para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Procesando disparadores para desktop-file-utils ...
Procesando disparadores para gnome-menus ...
Procesando disparadores para ureadahead ...
Configurando libmyth-0.25-0 (2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4) ...
Configurando libmythtv-perl (2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4) ...
Configurando mythtv-common (2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4) ...
dpkg: error al procesar mythtv-common (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 128
dpkg: problemas de dependencias impiden la configuración de mythtv-database:
 mythtv-database depende de mythtv-common; sin embargo:
 El paquete `mythtv-common' no está configurado todavía.
dpkg: error al procesar mythtv-database (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de mythtv-frontend:
 mythtv-frontend depende de mythtv-common; sin embargo:
 El paquete `mythtv-common' no está configurado todavía.
dpkg: error al procesar mythtv-frontend (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de mythtv-transcode-utils:
 mythtv-transcode-utils depende de mythtv-common; sin embargo:
 El paquete `mythtv-common' no está configurado todavía.
dpkg: error al procesar mythtv-transcode-utils (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de mythtv-backend:
 mythtv-backend depende de mythtv-common; sin embargo:
 El paquete `mythtv-common' no está configurado todavía.
 mythtv-backend depende de mythtv-transcode-utils; sin embargo:
 El paquete `mythtv-transcode-utils' no está configurado todavía.
dpkg: error al procesar mythtv-backend (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de mythtv:
 mythtv depende de mythtv-database; sin embargo:
 El paquete `mythtv-database' no está configurado todavía.
 mythtv depende de mythtv-frontend; sin embargo:
 El paquete `mythtv-frontend' no está configurado todavía.
 mythtv depende de mythtv-backend; sin embargo:
 El paquete `mythtv-backend' no está configurado todavía.
dpkg: error al procesar mythtv (--configure):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
 mythtv-common
 mythtv-database
 mythtv-frontend
 mythtv-transcode-utils
 mythtv-backend
 mythtv
Log ended: 2012-06-26  19:52:01[/I]

---

### Post by superm1 on 2012-06-28
OK since that isn't showing more information what you'll need to do is modify /var/lib/dpkg/info/mythtv-common.postinst.

On the third line add:

```
set -x

```

So it will look like this:

```
#!/bin/sh -e
. /usr/share/debconf/confmodule
set -x
case "$1" in

```

Then run ```
apt-get -f install
``` or ```
dpkg-reconfigure mythtv-common
```

There will be a lot of output, but it should show exactly which line in the script is causing a failure.

---

### Post by perevera on 2012-07-03
I'm sorry superm1, I appreciate your help but...

None of the logs show anything different after following your instructions.

---

### Post by perevera on 2012-07-06
I'm afraid this post will end up as all the rest regarding this subject: unsolved. None seems to have a solution to this problem...

---

### Post by tgm4883 on 2012-07-06
> **perevera said:**
> I'm afraid this post will end up as all the rest regarding this subject: unsolved. None seems to have a solution to this problem...

Are you sure it actually added and _**saved**_ the set -x in that file? If so, then it should print _**everything**_ that script is doing.

---

### Post by perevera on 2012-07-08
> **tgm4883 said:**
> Are you sure it actually added and _**saved**_ the set -x in that file? If so, then it should print _**everything**_ that script is doing.

I'm sure. The only relevant info is:

[I]Log started: 2012-07-08  11:59:20
Configurando mythtv-common (2:0.25.0+fixes.20120622.73bc45e-0ubuntu0mythbuntu4) ...
dpkg: error al procesar mythtv-common (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 128[/I]

Maybe it would help to know what means this error 128.

---

### Post by davehill1 on 2012-12-26
I got this error today when upgrading my mythtv packages.  I came across this post and repeated the steps suggested earlier and also did not see any extra output.  Then, I realized this is failing on the config script.  so I added a 'set -x' in mythtv-common.config and this is what I see:

> dhill@davetv:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
11 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mythtv-common (2:0.25.3+fixes.20121219.18c793a-0ubuntu0mythbuntu3) ...
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ CONFIG=/etc/mythtv/mysql.txt
+ [ -e /etc/mythtv/mysql.txt ]
+ sed -n -e s/^\(str  *\)\?DBName=\(.*\)$/\2/gp; /etc/mythtv/mysql.txt
+ db_set mythtv/mysql_mythtv_dbname mythconverg
+ _db_cmd SET mythtv/mysql_mythtv_dbname mythconverg
+ _db_internal_IFS= 	

+ IFS= 
+ printf %s\n SET mythtv/mysql_mythtv_dbname mythconverg
+ IFS= 	

+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?DBUserName=\(.*\)$/\2/gp; /etc/mythtv/mysql.txt
+ db_set mythtv/mysql_mythtv_user mythtv
+ _db_cmd SET mythtv/mysql_mythtv_user mythtv
+ _db_internal_IFS= 	

+ IFS= 
+ printf %s\n SET mythtv/mysql_mythtv_user mythtv
+ IFS= 	

+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?DBPassword=\(.*\)$/\2/gp; /etc/mythtv/mysql.txt
+ db_set mythtv/mysql_mythtv_password mythtv
mythtv
+ _db_cmd SET mythtv/mysql_mythtv_password mythtv
mythtv
+ _db_internal_IFS= 	

+ IFS= 
+ printf %s\n SET mythtv/mysql_mythtv_password mythtv
mythtv
+ IFS= 	

+ IFS=
 read -r _db_internal_line
+ RET=value set
+ return 0
+ sed -n -e s/^\(str  *\)\?DBHostName=\(.*\)$/\2/gp; /etc/mythtv/mysql.txt
+ db_set mythtv/mysql_host localhost
+ _db_cmd SET mythtv/mysql_host localhost
+ _db_internal_IFS= 	

+ IFS= 
+ printf %s\n SET mythtv/mysql_host localhost
+ IFS= 	

+ IFS=
 read -r _db_internal_line
+ RET=20 Unsupported command "mythtv" (full line was "mythtv") received from confmodule.
+ return 20
dpkg: error processing mythtv-common (--configure):
 subprocess installed post-installation script returned error exit status 20
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythgallery:No apport report written because the error message indicates its a followup error from a previous failure.



---

