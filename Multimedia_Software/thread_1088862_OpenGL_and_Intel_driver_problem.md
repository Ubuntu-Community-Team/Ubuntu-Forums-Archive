---
title: "OpenGL and Intel driver problem"
date: 2009-03-06
forum: Multimedia Software
---

### Post by Vishesh on 2009-03-06
Hi
I'm having some problems with my Intel G35 graphic card. 

I downloaded the xserver-xorg-intel package and configured xorg.conf to use the "intel" driver (The display works fine even if I don't). When I do glxinfo | grep OpenGL this is what I get - 

```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965G 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:

```and it shows that directRendering is enabled - 
```
vishesh@vishesh-desktop:~$ glxinfo                     
name of display: :0.0                                  
display: :0  screen: 0                                 
direct rendering: Yes                                  
server glx vendor string: SGI                          
server glx version string: 1.2                         
server glx extensions:                                 
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,     
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample,          
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group                           
client glx vendor string: SGI                                                 
client glx version string: 1.4                                                
client glx extensions:         

```But openGL applications dont seem to work properly. I get low frame rates (500-700) and the application seems all buggy, and there is the fact that It shows that I am using OpenGL v .14 Mesa, whereas I want atleast 2.0. 

A simple application which displays a square runs at a frame rate of about 170-350.
```

int width = 50;
glTranslatef( 100.0f, 100.0f, 0.0f );
    glBegin(GL_QUADS);
        glColor4f( 0.5, 0.5, 1.0, 1.0 );
        glVertex3f( 0, 0, 0 );
        glVertex3f( width, 0, 0 );
        glVertex3f( width, width, 0 );
        glVertex3f( 0, width, 0 );
    glEnd();

```Even glxgears gives me average frame rate of about 700. 
Does anyone have any ideas as to why this might be happening ? I really need OpenGL v 2.0 and my graphic card clearly supports it.
[http://www.intel.com/products/desktop/chipsets/g35/g35-overview.htm](http://www.intel.com/products/desktop/chipsets/g35/g35-overview.htm)

---

### Post by cariboo on 2009-03-06
You may want to update to a more current version of Ubuntu. I have Intrepid on my Intel Atom powered media center, I get about the same fps, running glxgears.

Jim

---

### Post by Vishesh on 2009-03-06
> **cariboo907 said:**
> You may want to update to a more current version of Ubuntu. I have Intrepid on my Intel Atom powered media center, I get about the same fps, running glxgears.

Jim

I'm using Ubuntu 8.10/ Kubuntu.

I get the same results on both. ( I just bought this PC about 10 days ago, so I just installed everything)

---

### Post by Vishesh on 2009-03-07
Bump !!

Come on someone must have a solution .. :-(

---

### Post by Vishesh on 2009-03-09
double bump !!

---

### Post by HeWhoE on 2009-03-19
I wish we could go back to the i810 driver.  In combination with 945resolution (to fix a resolution problem on my widescreen monitor) it was smooth and responsive.  

With the new xserver-xorg-intel driver, videos lag in mplayer and I get a lot of blinking behavior in compiz.  

I didn't have these nasty problems with the i810 driver!

---

### Post by mttman on 2009-03-28
I wanted to do the same thing. check out this thread

[http://ubuntuforums.org/showthread.php?t=1061331](http://ubuntuforums.org/showthread.php?t=1061331)

---

