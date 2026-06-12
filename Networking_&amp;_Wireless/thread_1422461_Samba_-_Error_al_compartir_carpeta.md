---
title: "Samba - Error al compartir carpeta"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by animusvirtus on 2010-03-05
Una vez instalado los paquetes de samba, samba-common, smbclient, los paquetes de nautilus para compartir de archivos (como nautilus-share, entre otros), intente compartir una carpeta, pero recibí el siguiente error:

"El parámetro de prueba de Samba devolvió el error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
    No such file or directory
Error loading services."

La configuración que tengo en el archivo smb.conf es la que viene por defecto tras la instalación de Ubuntu Netbook Remix.

A ver si alguien que le haya pasado o que entienda lo que el mensaje de error dice, me puede echar una mano.

---

