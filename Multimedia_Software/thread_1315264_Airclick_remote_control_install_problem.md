---
title: "Airclick remote control install problem"
date: 2009-11-05
forum: Multimedia Software
---

### Post by niccoc1603 on 2009-11-05
I'm tring to install the Airclick Remote control 0.7.1 ([http://ubuntuforums.org/showthread.php?t=504906](http://ubuntuforums.org/showthread.php?t=504906)) but i'm having this problem when make:

```

niccco@niccopc:~/Desktop/airclick-0.7.1$ make                                   
make  all-recursive                                                             
make[1]: Entering directory `/home/niccco/Desktop/airclick-0.7.1'               
Making all in src                                                               
make[2]: Entering directory `/home/niccco/Desktop/airclick-0.7.1/src'           
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
In file included from airclick.h:32,
                 from main.cpp:1:
logger.h: In member function ‘bool logger_basic_simple_rotation_policy<char_type, traits_type>::rotate(std::basic_ofstream<char_type, traits_type>&, const std::string&, const std::string&, const std::string&) [with char_type = char, traits_type = std::char_traits<char>]’:
main.cpp:514:   instantiated from here
logger.h:293: error: invalid conversion from ‘const char*’ to ‘char*’
main.cpp: At global scope:
main.cpp:514: fatal error: opening dependency file .deps/main.Tpo: Permission denied
compilation terminated.
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/niccco/Desktop/airclick-0.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/niccco/Desktop/airclick-0.7.1'
make: *** [all] Error 2

```

I'm a very linux newbie please help me! :D

---

### Post by niccoc1603 on 2009-11-06
anyone?

---

### Post by fizikz on 2009-11-20
I am also having the same problem as I am trying to install airclick after upgrading to Ubuntu 9.10. I had it working before in 9.04 without any problems.

---

### Post by fizikz on 2009-11-21
In case others are struggling with this, I found a solution: 

In airclick's src directory find the file logger.h and on line 293 add "const " (not including quotation marks) in front of "char". This was sufficient to allow 'make' to complete without errors and as far as I can tell everything works as it should again. ;)

---

