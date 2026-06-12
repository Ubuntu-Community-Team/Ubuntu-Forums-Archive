---
title: "Camera Genius Eye 312"
date: 2014-03-04
forum: Multimedia Software
---

### Post by Andres_E._Parilli on 2014-03-04
Hi,

I was trying to install on ubuntu the Genius Camara model Eye 312, and i findo some threds about this with the status SOLVED:

[h=1][Cam eye 312 ]("http://ubuntuforums.org/showthread.php?t=845262")[/h]
The problem is that the problems has not solved yet...

On thread [#35]("http://ubuntuforums.org/showthread.php?t=845262&p=10474288#post10474288") some user said that with line willl work but it dosent :(, have anybody find a solution?
> 
[h=2]Re: Cam eye 312[/h][COLOR=#000000][INDENT][I][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **al-go** [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=10345927#post10345927")

Por consola:

**$ sudo apt-get install v4l2ucp** 


Luego de instalado **v4l2cup**, acceder a System > Preferences > Video4Linux Control Panel y ahi activamos el checkbox de Vflip ubicado en la parte inferior, cerramos y listo! Ah, y si también tienen el problemita de la imagen espejo, pueden corregirla tildando la ventanita de *mirror*. 


[/I]

Corrijo para que quede claro:

***$ sudo apt-get install v4l2cup*** (es v-corta, cuatro, ele, dos, cup)[/INDENT]
[/COLOR]
[INDENT]Last edited by Pan0ramix; February 19th, 2011 at [COLOR=#3E3E3E]07:56 PM[/COLOR].[/INDENT][INDENT]Saludos
Pan0ramix
[/INDENT]

---

