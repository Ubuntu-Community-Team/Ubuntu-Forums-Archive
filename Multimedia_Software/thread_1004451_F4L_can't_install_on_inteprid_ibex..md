---
title: "F4L can't install on inteprid ibex."
date: 2008-12-07
forum: Multimedia Software
---

### Post by dragos240 on 2008-12-07
Hey i tried to install F4L and i got this:
```
USER@ubuntu:~/f4l-0.2$ make
cd src/flagStonePort/transform-cxx-bsd/transform/ && make -f Makefile 
make[1]: Entering directory `/home/USER/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -fPIC -w -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o FSButtonEvent.o FSButtonEvent.cpp
In file included from FSButtonEvent.h:34,
                 from FSButtonEvent.cpp:22:
FSVector.h:35:17: error: new.h: No such file or directory
FSVector.h: In constructor ‘transform::FSVector<T>::FSVector(int) [with T = transform::FSActionObject*]’:
FSButtonEvent.h:152:   instantiated from here
FSVector.h:174: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]’:
FSButtonEvent.h:196:   instantiated from here
FSVector.h:275: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In constructor ‘transform::FSVector<T>::FSVector(int) [with T = transform::FSShapeObject*]’:
FSShape.h:75:   instantiated from here
FSVector.h:174: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]’:
FSShape.h:97:   instantiated from here
FSVector.h:275: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSShapeObject*]’:
FSShape.h:115:   instantiated from here
FSVector.h:204: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSActionObject*]’:
FSButtonEvent.cpp:104:   instantiated from here
FSVector.h:204: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::reserve(int) [with T = transform::FSActionObject*]’:
FSVector.h:271:   instantiated from ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]’
FSButtonEvent.h:196:   instantiated from here
FSVector.h:246: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::reserve(int) [with T = transform::FSShapeObject*]’:
FSVector.h:271:   instantiated from ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]’
FSShape.h:97:   instantiated from here
FSVector.h:246: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
make[1]: *** [FSButtonEvent.o] Error 1
make[1]: Leaving directory `/home/USER/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform-make_default] Error 2
```

What should i do?

---

### Post by dragos240 on 2008-12-07
[img]http://threadbomb.us/com/gallery/1_09_12_07_9_24_49.gif[/img]

---

### Post by nukleuzN on 2009-02-23
:mrgreen: bump :)

i got this: (only)
```
joachim@joachim-laptop-asus:~/f4l-0.2$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/joachim/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSAction.o FSAction.cpp
make[1]: g++: Command not found
make[1]: *** [FSAction.o] Error 127
make[1]: Leaving directory `/home/joachim/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
```

---

### Post by dviejo on 2009-03-05
> **nukleuzN said:**
> :mrgreen: bump :)

i got this: (only)
```
joachim@joachim-laptop-asus:~/f4l-0.2$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/joachim/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSAction.o FSAction.cpp
make[1]: g++: Command not found
make[1]: *** [FSAction.o] Error 127
make[1]: Leaving directory `/home/joachim/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
```


Hey, try to install g++ before ;)
sudo apt-get install g++

---

### Post by MichaelSammels on 2009-06-02
No,

I get this error as well, even with G++ installed.

---

### Post by MichaelSammels on 2009-06-02
My Error:

```
michael@ubuntu-linux:~/f4l-0.2.1$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/michael/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSAction.o FSAction.cpp
In file included from FSTransformObject.h:22,
                 from FSActionObject.h:34,
                 from FSAction.h:34,
                 from FSAction.cpp:22:
FSTransform.h:52:20: error: stdlib.h: No such file or directory
In file included from FSTransformObject.h:22,
                 from FSActionObject.h:34,
                 from FSAction.h:34,
                 from FSAction.cpp:22:
FSTransform.h:91: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:93: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:93: error: &#8216;size_t&#8217; has not been declared
In file included from FSInputStream.h:34,
                 from FSAction.cpp:24:
FSStream.h:59: error: &#8216;size_t&#8217; has not been declared
FSStream.h:70: error: &#8216;size_t&#8217; has not been declared
FSStream.h:85: error: &#8216;size_t&#8217; does not name a type
In file included from FSAction.cpp:24:
FSInputStream.h:41: error: &#8216;size_t&#8217; has not been declared
In file included from FSAction.cpp:25:
FSOutputStream.h:41: error: expected `)' before &#8216;numberOfBytes&#8217;
make[1]: *** [FSAction.o] Error 1
make[1]: Leaving directory `/home/michael/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
michael@ubuntu-linux:~/f4l-0.2.1$ sudo make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/michael/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSAction.o FSAction.cpp
In file included from FSTransformObject.h:22,
                 from FSActionObject.h:34,
                 from FSAction.h:34,
                 from FSAction.cpp:22:
FSTransform.h:52:20: error: stdlib.h: No such file or directory
In file included from FSTransformObject.h:22,
                 from FSActionObject.h:34,
                 from FSAction.h:34,
                 from FSAction.cpp:22:
FSTransform.h:91: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:93: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:93: error: &#8216;size_t&#8217; has not been declared
In file included from FSInputStream.h:34,
                 from FSAction.cpp:24:
FSStream.h:59: error: &#8216;size_t&#8217; has not been declared
FSStream.h:70: error: &#8216;size_t&#8217; has not been declared
FSStream.h:85: error: &#8216;size_t&#8217; does not name a type
In file included from FSAction.cpp:24:
FSInputStream.h:41: error: &#8216;size_t&#8217; has not been declared
In file included from FSAction.cpp:25:
FSOutputStream.h:41: error: expected `)' before &#8216;numberOfBytes&#8217;
make[1]: *** [FSAction.o] Error 1
make[1]: Leaving directory `/home/michael/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
michael@ubuntu-linux:~/f4l-0.2.1$ clear

michael@ubuntu-linux:~/f4l-0.2.1$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/michael/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSAction.o FSAction.cpp
In file included from FSTransformObject.h:22,
                 from FSActionObject.h:34,
                 from FSAction.h:34,
                 from FSAction.cpp:22:
FSTransform.h:52:20: error: stdlib.h: No such file or directory
In file included from FSTransformObject.h:22,
                 from FSActionObject.h:34,
                 from FSAction.h:34,
                 from FSAction.cpp:22:
FSTransform.h:91: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:92: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:93: error: &#8216;size_t&#8217; has not been declared
FSTransform.h:93: error: &#8216;size_t&#8217; has not been declared
In file included from FSInputStream.h:34,
                 from FSAction.cpp:24:
FSStream.h:59: error: &#8216;size_t&#8217; has not been declared
FSStream.h:70: error: &#8216;size_t&#8217; has not been declared
FSStream.h:85: error: &#8216;size_t&#8217; does not name a type
In file included from FSAction.cpp:24:
FSInputStream.h:41: error: &#8216;size_t&#8217; has not been declared
In file included from FSAction.cpp:25:
FSOutputStream.h:41: error: expected `)' before &#8216;numberOfBytes&#8217;
make[1]: *** [FSAction.o] Error 1
make[1]: Leaving directory `/home/michael/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
```

---

### Post by achase79 on 2009-06-19
do you have qt3-dev-tools and libqt3-mt-dev installed?

---

### Post by dragos240 on 2009-06-19
Lol!

---

### Post by dannymichel on 2009-07-30
> **achase79 said:**
> do you have qt3-dev-tools and libqt3-mt-dev installed?

have all that installed. still cant install
```
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:115:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.cpp:104:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSActionObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]&#8217;
FSButtonEvent.h:196:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSShapeObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]&#8217;
FSShape.h:97:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
make[1]: *** [FSButtonEvent.o] Error 1
make[1]: Leaving directory `/home/danny/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
danny@danny-desktop:~/f4l-0.2$ sudo apt-get update
[sudo] password for danny: 
Ign http://ftp.osuosl.org jaunty/ Release.gpg
Ign http://ftp.osuosl.org jaunty/ Translation-en_US                            
Ign http://ftp.osuosl.org jaunty/ Release                                      
Ign http://linux.getdropbox.com jaunty Release.gpg                             
Ign http://linux.getdropbox.com jaunty/main Translation-en_US                  
Ign http://ftp.osuosl.org jaunty/ Packages                                     
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Ign http://archive.ubuntu.com jaunty/main Translation-en_US                    
Hit http://ftp.osuosl.org jaunty/ Packages                                     
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Hit http://download.virtualbox.org jaunty Release.gpg                          
Ign http://download.virtualbox.org jaunty/non-free Translation-en_US           
Ign http://linux.getdropbox.com jaunty Release                                 
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Hit http://ubuntusatanic.org jaunty Release.gpg                                
Ign http://ubuntusatanic.org jaunty/main Translation-en_US                     
Ign http://linux.getdropbox.com jaunty/main Packages                           
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US                
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US              
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US              
Hit http://archive.ubuntu.com jaunty-updates Release.gpg                       
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US            
Hit http://packages.medibuntu.org jaunty Release                               
Hit http://download.virtualbox.org jaunty Release                              
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US      
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US      
Hit http://archive.ubuntu.com jaunty-proposed Release.gpg                      
Ign http://archive.ubuntu.com jaunty-proposed/universe Translation-en_US       
Ign http://download.opensuse.org ./ Release.gpg                                
Hit http://linux.getdropbox.com jaunty/main Packages                           
Ign http://ppa.launchpad.net jaunty/universe Translation-en_US                 
Get:1 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Hit http://ubuntusatanic.org jaunty Release                                    
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://packages.medibuntu.org jaunty/free Packages                         
Ign http://archive.ubuntu.com jaunty-proposed/main Translation-en_US           
Ign http://archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US     
Ign http://archive.ubuntu.com jaunty-proposed/restricted Translation-en_US     
Hit http://archive.ubuntu.com jaunty-backports Release.gpg                     
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com jaunty-backports/main Translation-en_US          
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-en_US    
Hit http://download.virtualbox.org jaunty/non-free Packages                    
Hit http://deb.opera.com etch Release.gpg                                      
Ign http://deb.opera.com etch/non-free Translation-en_US                       
Ign http://download.opensuse.org ./ Translation-en_US                          
Ign http://download.opensuse.org ./ Release.gpg                                
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:2 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://download.opensuse.org ./ Translation-en_US                          
Hit http://ubuntusatanic.org jaunty/main Packages                              
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-en_US    
Hit http://archive.ubuntu.com jaunty Release                                   
Hit http://archive.ubuntu.com jaunty-updates Release                           
Hit http://archive.ubuntu.com jaunty-proposed Release                          
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://ppa.launchpad.net jaunty/universe Translation-en_US                 
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Hit http://deb.opera.com etch Release                                          
Hit http://archive.ubuntu.com jaunty-backports Release                         
Ign http://download.opensuse.org ./ Release                                    
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Get:3 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Hit http://archive.ubuntu.com jaunty/main Packages                             
Hit http://archive.ubuntu.com jaunty/universe Packages                         
Hit http://archive.ubuntu.com jaunty/restricted Packages                       
Hit http://archive.ubuntu.com jaunty/multiverse Packages                       
Hit http://archive.ubuntu.com jaunty-updates/universe Packages                 
Hit http://archive.ubuntu.com jaunty-updates/main Packages                     
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages               
Ign http://deb.opera.com etch/non-free Packages                                
Ign http://download.opensuse.org ./ Release                                    
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Get:4 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages               
Hit http://archive.ubuntu.com jaunty-proposed/universe Packages                
Hit http://archive.ubuntu.com jaunty-proposed/main Packages                    
Hit http://archive.ubuntu.com jaunty-proposed/multiverse Packages              
Hit http://archive.ubuntu.com jaunty-proposed/restricted Packages              
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://download.opensuse.org ./ Packages                                   
Hit http://deb.opera.com etch/non-free Packages                                
Hit http://archive.ubuntu.com jaunty-backports/universe Packages               
Hit http://archive.ubuntu.com jaunty-backports/main Packages                   
Hit http://archive.ubuntu.com jaunty-backports/multiverse Packages             
Hit http://archive.ubuntu.com jaunty-backports/restricted Packages             
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://download.opensuse.org ./ Packages                                   
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Get:5 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Hit http://download.opensuse.org ./ Packages                                   
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://ppa.launchpad.net jaunty Release                          
Hit http://ppa.launchpad.net jaunty Release                          
Hit http://ppa.launchpad.net jaunty Release                                    
Hit http://ppa.launchpad.net jaunty Release                                    
Hit http://ppa.launchpad.net jaunty Release                                    
Hit http://ppa.launchpad.net jaunty Release                                    
Get:6 http://ppa.launchpad.net jaunty Release [74.6kB]                         
Hit http://download.opensuse.org ./ Packages                                   
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US              
Get:7 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:8 http://ppa.launchpad.net jaunty Release [74.7kB]               
Hit http://wine.budgetdedicated.com jaunty Release                        
Hit http://ppa.launchpad.net jaunty Release                               
Hit http://ppa.launchpad.net jaunty Release           
Hit http://ppa.launchpad.net jaunty Release           
Hit http://ppa.launchpad.net jaunty Release           
Hit http://ppa.launchpad.net jaunty Release           
Get:9 http://ppa.launchpad.net jaunty Release [74.7kB]
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Get:10 http://ppa.launchpad.net jaunty Release [74.7kB]                        
Hit http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://ppa.launchpad.net jaunty Release                                 
Hit http://ppa.launchpad.net jaunty Release            
Hit http://ppa.launchpad.net jaunty Release            
Hit http://ppa.launchpad.net jaunty Release            
Hit http://ppa.launchpad.net jaunty Release            
Hit http://ppa.launchpad.net jaunty Release            
Hit http://ppa.launchpad.net jaunty Release            
Hit http://ppa.launchpad.net jaunty Release            
Hit http://ppa.launchpad.net jaunty Release            
Get:11 http://ppa.launchpad.net jaunty Release [74.7kB]                
Hit http://ppa.launchpad.net jaunty Release                            
Hit http://ppa.launchpad.net jaunty/main Packages                      
Hit http://ppa.launchpad.net jaunty/main Packages                      
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Packages                   
Ign http://ppa.launchpad.net jaunty/universe Packages
Get:12 http://ppa.launchpad.net jaunty/main Packages [3093B]
Ign http://ppa.launchpad.net hardy/main Packages      
Get:13 http://ppa.launchpad.net jaunty/main Packages [3286B]         
Ign http://ppa.launchpad.net jaunty/main Packages                    
Ign http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/universe Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Packages
Get:14 http://ppa.launchpad.net jaunty/main Packages [1634B]
Get:15 http://ppa.launchpad.net jaunty/main Packages [2057B]         
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://ppa.launchpad.net jaunty/main Packages                          
Ign http://ppa.launchpad.net jaunty/main Packages                          
Ign http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Get:16 http://ppa.launchpad.net jaunty/main Packages [7643B]
Hit http://ppa.launchpad.net jaunty/main Packages    
Hit http://ppa.launchpad.net jaunty/main Packages    
Hit http://ppa.launchpad.net jaunty/main Packages                    
Hit http://ppa.launchpad.net jaunty/universe Packages                    
Hit http://ppa.launchpad.net hardy/main Packages                         
Hit http://ppa.launchpad.net jaunty/main Packages                        
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Get:17 http://dl.google.com stable Release.gpg [191B]                          
Ign http://dl.google.com stable/non-free Translation-en_US
Get:18 http://dl.google.com testing Release.gpg [191B]
Ign http://dl.google.com testing/non-free Translation-en_US
Get:19 http://dl.google.com stable Release [1308B]
Get:20 http://dl.google.com testing Release [1297B]
Get:21 http://dl.google.com stable/non-free Packages [966B]
Get:22 http://dl.google.com testing/non-free Packages [734B]
Fetched 397kB in 24s (16.3kB/s)                                                
Reading package lists... Done
danny@danny-desktop:~/f4l-0.2$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  build-essential dpkg-dev{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 650kB of archives. After unpacking 2040kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com jaunty/main dpkg-dev 1.14.24ubuntu1 [643kB]
Get:2 http://archive.ubuntu.com jaunty/main build-essential 11.4 [7170B]
Fetched 650kB in 1s (584kB/s)       
Selecting previously deselected package dpkg-dev.
(Reading database ... 205360 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.14.24ubuntu1_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_amd64.deb) ...
Processing triggers for man-db ...
Setting up dpkg-dev (1.14.24ubuntu1) ...
Setting up build-essential (11.4) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

danny@danny-desktop:~/f4l-0.2$ ./configure
bash: ./configure: No such file or directory
danny@danny-desktop:~/f4l-0.2$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/danny/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSButtonEvent.o FSButtonEvent.cpp
In file included from FSButtonEvent.h:34,
                 from FSButtonEvent.cpp:22:
FSVector.h:35:17: error: new.h: No such file or directory
FSVector.h: In constructor &#8216;transform::FSVector<T>::FSVector(int) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.h:152:   instantiated from here
FSVector.h:174: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.h:196:   instantiated from here
FSVector.h:275: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In constructor &#8216;transform::FSVector<T>::FSVector(int) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:75:   instantiated from here
FSVector.h:174: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:97:   instantiated from here
FSVector.h:275: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:115:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.cpp:104:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSActionObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]&#8217;
FSButtonEvent.h:196:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSShapeObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]&#8217;
FSShape.h:97:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
make[1]: *** [FSButtonEvent.o] Error 1
make[1]: Leaving directory `/home/danny/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
danny@danny-desktop:~/f4l-0.2$ apt-get install qt3-dev-tools libqt3-mt-dev g++
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
danny@danny-desktop:~/f4l-0.2$ sudo apt-get install qt3-dev-tools libqt3-mt-dev g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
qt3-dev-tools is already the newest version.
libqt3-mt-dev is already the newest version.
libqt3-mt-dev set to manually installed.
g++ is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danny@danny-desktop:~/f4l-0.2$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/danny/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSButtonEvent.o FSButtonEvent.cpp
In file included from FSButtonEvent.h:34,
                 from FSButtonEvent.cpp:22:
FSVector.h:35:17: error: new.h: No such file or directory
FSVector.h: In constructor &#8216;transform::FSVector<T>::FSVector(int) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.h:152:   instantiated from here
FSVector.h:174: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.h:196:   instantiated from here
FSVector.h:275: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In constructor &#8216;transform::FSVector<T>::FSVector(int) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:75:   instantiated from here
FSVector.h:174: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:97:   instantiated from here
FSVector.h:275: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:115:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.cpp:104:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSActionObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]&#8217;
FSButtonEvent.h:196:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSShapeObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]&#8217;
FSShape.h:97:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
make[1]: *** [FSButtonEvent.o] Error 1
make[1]: Leaving directory `/home/danny/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
danny@danny-desktop:~/f4l-0.2$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/danny/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSButtonEvent.o FSButtonEvent.cpp
In file included from FSButtonEvent.h:34,
                 from FSButtonEvent.cpp:22:
FSVector.h:35:17: error: new.h: No such file or directory
FSVector.h: In constructor &#8216;transform::FSVector<T>::FSVector(int) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.h:152:   instantiated from here
FSVector.h:174: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.h:196:   instantiated from here
FSVector.h:275: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In constructor &#8216;transform::FSVector<T>::FSVector(int) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:75:   instantiated from here
FSVector.h:174: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:97:   instantiated from here
FSVector.h:275: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSShapeObject*]&#8217;:
FSShape.h:115:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSActionObject*]&#8217;:
FSButtonEvent.cpp:104:   instantiated from here
FSVector.h:204: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSActionObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]&#8217;
FSButtonEvent.h:196:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSActionObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
FSVector.h: In member function &#8216;void transform::FSVector<T>::reserve(int) [with T = transform::FSShapeObject*]&#8217;:
FSVector.h:271:   instantiated from &#8216;void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]&#8217;
FSShape.h:97:   instantiated from here
FSVector.h:246: error: no matching function for call to &#8216;operator new(long unsigned int, transform::FSShapeObject**&)&#8217;
<built-in>:0: note: candidates are: void* operator new(long unsigned int)
make[1]: *** [FSButtonEvent.o] Error 1
make[1]: Leaving directory `/home/danny/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2
danny@danny-desktop:~/f4l-0.2$ 

```

---

