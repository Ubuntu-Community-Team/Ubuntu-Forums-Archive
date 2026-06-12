---
title: "Dual Screen - Running simultaneously Boxee and GDM at startup"
date: 2010-03-04
forum: Multimedia Software
---

### Post by gastounage on 2010-03-04
Hi everyone, 

I have a 24inch monitor and a LCD TV both connected to my graphic card, by HDMI for the TV and DVI for the monitor.

Here's my problem: I would like GDM and [Boxee]("http://en.wikipedia.org/wiki/Boxee") to start simultaneously when I start my computer, Boxee displayed on my TV and GDM on my monitor.

I made some research and I unfortunately did not found anything about starting a graphical software and GDM in parrallel (two separated DISPLAY).

I have no particular attachment to GDM so if you think it would be easier to use the classic login prompt or another Display-Manager do not hesitate, The crux is to have an authentification system before accessing to Gnome and an detached Boxee running on my TV.

Do you have any idea(s) ?

(Ubuntu 9.10 64bits / nvidia 9400GT HDMI+DVI)

Regards,

------------------------------------------------------------------
(FR)

Bonjour à tous,

Je possède un écran 24" ainsi qu'une télé, ils sont tous les deux connectés sur ma carte graphique via l'HDMI pour la télé et le DVI pour mon écran.

Voici ma problématique, je souhaiterai qu'au démarrage : GDM s'affiche sur mon écran et [Boxee]("http://en.wikipedia.org/wiki/Boxee") sur ma télé.

Après quelques recherches je n'ai hélas rien trouvé concernant la possibilité d'exécuter une application graphique en parallèle de GDM (donc sur deux DISPLAY différents).

Je n'ai aucune adhérence avec GDM donc si vous pensez qu'il serait plus simple d'utiliser le prompt de login command-line ou un autre Display-Manager n'hésitez pas. L'essentiel étant d'avoir un système d'authentification avant d'accéder à Gnome et un Boxee indépendant sur la TV. 

Est-ce que vous auriez une idée ?

(Ubuntu 9.10 64bits / nvidia 9400GT HDMI+DVI)

Merci.

---

### Post by tchekyfelb7 on 2011-01-07
> **gastounage said:**
> Hi everyone, I have a 24inch monitor and a LCD TV both connected to my graphic card, by HDMI for the TV and DVI for the monitor.Here's my problem: I would like GDM and [Boxee](http://en.wikipedia.org/wiki/Boxee) to start simultaneously when I start my computer, Boxee displayed on my TV and GDM on my monitor.I made some research and I unfortunately did not found anything about starting a graphical [[COLOR=#000000]software[/COLOR]](http://www.**********************/qt-conversion-guide/qt-to-blackberrry-guide.html) and GDM in parrallel (two separated DISPLAY).I have no particular attachment to GDM so if you think it would be easier to use the classic login prompt or another Display-Manager do not hesitate, The crux is to have an authentification system before accessing to Gnome and an detached Boxee running on my TV.Do you have any idea(s) ?(Ubuntu 9.10 64bits / nvidia 9400GT HDMI+DVI)Regards,------------------------------------------------------------------(FR)Bonjour ? tous,Je poss?de un ?cran 24" ainsi qu'une t?l?, ils sont tous les deux connect?s sur ma carte graphique via l'HDMI pour la t?l? et le DVI pour mon ?cran.Voici ma probl?matique, je souhaiterai qu'au d?marrage : GDM s'affiche sur mon ?cran et [Boxee](http://en.wikipedia.org/wiki/Boxee) sur ma t?l?.Apr?s quelques recherches je n'ai h?las rien trouv? concernant la possibilit? d'ex?cuter une application graphique en parall?le de GDM (donc sur deux DISPLAY diff?rents).Je n'ai aucune adh?rence avec GDM donc si vous pensez qu'il serait plus simple d'utiliser le prompt de login command-line ou un autre Display-Manager n'h?sitez pas. L'essentiel ?tant d'avoir un syst?me d'authentification avant d'acc?der ? Gnome et un Boxee ind?pendant sur la TV. Est-ce que vous auriez une id?e ?(Ubuntu 9.10 64bits / nvidia 9400GT HDMI+DVI)Merci.It's very detailed, Many thanks to your description! This is what I'm looking for.

---

### Post by BicyclerBoy on 2011-01-07
You can have two separate X screens on the same GPU .
This is more flexible w.r.t. video modes.
It is easier to control the app launch display with separate X screens.

What's the problem with gdm running on them both..

I have MythTV start full screen on secondary display & normal gnome desktop on the other..

---

