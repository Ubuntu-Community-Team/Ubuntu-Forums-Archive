---
title: "problem with opengl .. please I need HELP"
date: 2010-01-17
forum: Multimedia Software
---

### Post by wildammiras on 2010-01-17
Hi ,
I'm trying to work with the robocup simulator (SIMSPARK) , but it doesn't work. Really i don't know why.
The terminal show me the following error and i think that the problem is from UBUNTU and OPENGL : 


(spark.rb) sparkResetLogging removing all log targets
(spark.rb) sparkEnableLog logTarget=:cerr logType=eError
(Light) ERROR: OpenGLServer not found
(Light) ERROR: OpenGLServer not found
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.
(Material2DTexture) ERROR: cannot find TextureServer
(Material2DTexture) ERROR: OpenGLServer not found.


PLEASE, if someone can help me .. I really need his help .
Thanks.

---

### Post by MonXX on 2010-01-27
Hey, these aren't actual errors, more like warnings.

The latest version of spark/rcssserver3 (0.2 and 0.6.3) split the simulation from the visualization: the main programs now are rcssserver3d (simulator) and rcssmonitor3d (visualization). The script rcsoccersim3d runs both of them and probably gives you what you expect when running 'simspark'.

For future reverence, you're probably better off posting these questions on the robocup 3d simulation mailinglist: [https://lists.sourceforge.net/lists/listinfo/sserver-three-d](https://lists.sourceforge.net/lists/listinfo/sserver-three-d)

---

### Post by wildammiras on 2010-02-02
:p:p:p:p:p:p:p:p
Thank you [MonXX]("http://ubuntuforums.org/member.php?u=83835") ... you make me Happy, because now simspark works .
PLZ, if you have any documents about Simspark, PLZ send them to me at [EMAIL="wildammiras@yahoo.fr"]wildammiras@yahoo.fr[/EMAIL] .
THANK YOU ....

---

