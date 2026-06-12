---
title: "Amarok 2 won't show a playlist"
date: 2009-01-25
forum: Multimedia Software
---

### Post by moredhel on 2009-01-25
I have recently tried to install amarok 2.0.1 but I can't seem to get it to work. I added
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
to the sources list and then did

sudo aptitude install amarok-kde4

However whenever I start it up, the only thing that shows are the controls at the top,i.e. I dont have a playlist or anything, and right clicking does nothing. This is what I get: [IMG]http://i42.tinypic.com/14o38er.jpg[/IMG]

I tried running it from a terminal and got:

```
sim@wensleydale:~$ amarok 
amarok(8889) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics()                   
Object::connect:  (receiver name: 'MainWindow')                              
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!                                                         
Couldn't resolve property: radialGradient3986                                               
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!                                                         
Couldn't resolve property: radialGradient3986                                               
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
amarok(8889) Plasma::Applet::save: saving to "1"                                            
amarok(8889) Context::ContextView::setContainment: "" Line:  599                            
amarok(8889) Plasma::ThemePrivate::config: using theme for app "amarok"                     
amarok(8889) Plasma::Applet::save: saving to "2"                                            
amarok(8889) Plasma::Applet::save: saving to "3"                                            
amarok(8889) Plasma::Applet::save: saving to "4"                                            
amarok(8889) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated                           
amarok(8889) Context::ColumnContainment::insertInGrid: "" Line:  603                        
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!                                                         
Couldn't resolve property: radialGradient3986                                               
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!
```

I really dont know enough to know what is going wrong, can anybody help?
Thanks

---

### Post by moredhel on 2009-01-25
bump

---

### Post by moredhel on 2009-02-01
no one?

---

### Post by mrcsparker on 2009-02-03
Same problem here.

---

### Post by Chegevara on 2009-02-21
> **moredhel said:**
> I have recently tried to install amarok 2.0.1 but I can't seem to get it to work. I added
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
to the sources list and then did

sudo aptitude install amarok-kde4

However whenever I start it up, the only thing that shows are the controls at the top,i.e. I dont have a playlist or anything, and right clicking does nothing. This is what I get: [IMG]http://i42.tinypic.com/14o38er.jpg[/IMG]

I tried running it from a terminal and got:

```
sim@wensleydale:~$ amarok 
amarok(8889) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics()                   
Object::connect:  (receiver name: 'MainWindow')                              
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!                                                         
Couldn't resolve property: radialGradient3986                                               
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!                                                         
Couldn't resolve property: radialGradient3986                                               
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
QWidget::insertAction: Attempt to insert null action                                        
amarok(8889) Plasma::Applet::save: saving to "1"                                            
amarok(8889) Context::ContextView::setContainment: "" Line:  599                            
amarok(8889) Plasma::ThemePrivate::config: using theme for app "amarok"                     
amarok(8889) Plasma::Applet::save: saving to "2"                                            
amarok(8889) Plasma::Applet::save: saving to "3"                                            
amarok(8889) Plasma::Applet::save: saving to "4"                                            
amarok(8889) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated                           
amarok(8889) Context::ColumnContainment::insertInGrid: "" Line:  603                        
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!                                                         
Couldn't resolve property: radialGradient3986                                               
link XMLID_7_ hasn't been detected!                                                         
link XMLID_7_ hasn't been detected!
```

I really dont know enough to know what is going wrong, can anybody help?
Thanks

I had the same problem . If I can say problem ? Solving is very easy and I hope that will help you ;o) 

 One possibility I've heard of is that one of the panels got dragged over all the other ones, covering them. Is it possible to drag one of the inside edges to uncover some panels? Usually you can see three little dots on the edge of a panel to show you where to click and drag.

For explanation three little dots are on right side open amarok window.

---

### Post by markbuntu on 2009-02-21
That PPA is for testing the bleeding edge. Thank you for testing. Have you filed a bug report?

---

### Post by Chegevara on 2009-02-22
no

---

### Post by euchrid33 on 2009-03-13
I've got a similar problem, same blank Amarok 2 window.  It used to work fine, but now it doesn't.  I'm not sure what I might have installed or changed to cause this to happen.  

Has there not been any progress in solving this?

---

### Post by registringsucks on 2009-04-07
I DID had this problem as well.
The solution is so simple it'll make you crazy...

Have a <very> good look at the blank part of the screendump.
Look at 2/3rd to the right, and near the middle from top till bottom.
Here you'll see 3 very small dots below each other.

Click the dots and drag them to the left or right and the problem is solved.

---

