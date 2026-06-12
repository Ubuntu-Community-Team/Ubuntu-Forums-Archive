---
title: "Problems compiling festival"
date: 2013-11-22
forum: Multimedia Software
---

### Post by stephverez on 2013-11-22
Hi,

I'm willing to compile [Festival]("http://www.cstr.ed.ac.uk/projects/festival/") (text to speech) as a library so I can use it in my own programs.

When trying to compile the speech_tools (after the ./configure went well) that's what i get:

```
parouuu@parouuu-ubuntu:~/fes/speech_tools$ make
Check system type
Remake modincludes.inc
    NATIVE_AUDIO
        ok
    EDITLINE
        config/modules/editline.mak
    SIOD
        siod/siod.mak
    WAGON
        stats/wagon/wagon.mak
    SCFG
        grammar/scfg/scfg.mak
    WFST
        grammar/wfst/wfst.mak
    OLS
        stats/ols.mak
    RXP
        rxp/rxp.mak
    LINUX16_AUDIO
        config/modules/linux16_audio.mak
Making in directory ./siod ...
making dependencies -- siodeditline.c el_complete.c editline.c el_sys_unix.c slib.cc slib_core.cc slib_doc.cc slib_file.cc slib_format.cc slib_list.cc slib_math.cc slib_sys.cc slib_server.cc slib_str.cc slib_xtr.cc slib_repl.cc siod_fringe.cc siod_server.cc io.cc trace.cc EST_SiodServer.cc siod.cc siod_est.cc 
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib.cc
slib.cc: In function &#8216;int f_getc(FILE*)&#8217;:
slib.cc:1523:13: warning: variable &#8216;dflag&#8217; set but not used [-Wunused-but-set-variable]
 {long iflag,dflag;
             ^
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_core.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_doc.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_file.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_format.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_list.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_math.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_sys.cc
slib_sys.cc: In function &#8216;obj* lsystem(LISP)&#8217;:
slib_sys.cc:36:31: warning: ignoring return value of &#8216;int system(const char*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
     system(get_c_string(name));
                               ^
slib_sys.cc: In function &#8216;obj* lchdir(LISP, LISP)&#8217;:
slib_sys.cc:57:13: warning: ignoring return value of &#8216;int chdir(const char*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
  chdir(home);
             ^
slib_sys.cc:62:43: warning: ignoring return value of &#8216;int chdir(const char*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
  chdir(get_c_string(leval(car(args),env)));
                                           ^
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_server.cc
slib_server.cc: In function &#8216;obj* siod_send_lisp_to_client(LISP)&#8217;:
slib_server.cc:43:36: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
  write(siod_server_socket,"LP\n",3);
                                    ^
slib_server.cc: In function &#8216;void sock_acknowledge_error()&#8217;:
slib_server.cc:61:36: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
  write(siod_server_socket,"ER\n",3);
                                    ^
slib_server.cc: In function &#8216;void acknowledge_sock_print(LISP)&#8217;:
slib_server.cc:73:39: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
     write(siod_server_socket,"OK\n",3);
                                       ^
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_str.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_xtr.cc
slib_xtr.cc: In function &#8216;obj* fast_read(LISP)&#8217;:
slib_xtr.cc:465:8: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
      f);
        ^
slib_xtr.cc:471:30: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
       fread(tkbuffer,len,1,f);
                              ^
slib_xtr.cc: In function &#8216;long int get_long(FILE*)&#8217;:
slib_xtr.cc:345:28: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
  fread(&i,sizeof(long),1,f);
                            ^
slib_xtr.cc: In function &#8216;obj* array_fast_read(int, LISP)&#8217;:
slib_xtr.cc:523:49: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
       fread(ptr->storage_as.string.data,len,1,f);
                                                 ^
slib_xtr.cc:533:68: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
       fread(ptr->storage_as.double_array.data,sizeof(double),len,f);
                                                                    ^
slib_xtr.cc:543:64: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
       fread(ptr->storage_as.long_array.data,sizeof(long),len,f);
                                                                ^
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include slib_repl.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include siod_fringe.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include siod_server.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include io.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include trace.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include EST_SiodServer.cc
gcc -c -fno-implicit-templates -O3 -fPIC -Wall -DSUPPORT_EDITLINE -I../include -DINSTANTIATE_TEMPLATES siod.cc
In file included from ../include/EST_THash.h:46:0,
                 from siod.cc:31:
../include/EST_TIterator.h: In instantiation of &#8216;EST_TStructIterator<Container, IPointer, Entry>::EST_TStructIterator(const Container&) [with Container = EST_THash<EST_String, EST_Regex*>; IPointer = EST_THash<EST_String, EST_Regex*>::IPointer_s; Entry = EST_Hash_Pair<EST_String, EST_Regex*>]&#8217;:
siod.cc:47:3:   required from here
../include/EST_TIterator.h:212:17: error: &#8216;begin&#8217; was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
     { begin(over); }
                 ^
../include/EST_TIterator.h:212:17: note: declarations in dependent base &#8216;EST_TIterator<EST_THash<EST_String, EST_Regex*>, EST_THash<EST_String, EST_Regex*>::IPointer_s, EST_Hash_Pair<EST_String, EST_Regex*> >&#8217; are not found by unqualified lookup
../include/EST_TIterator.h:212:17: note: use &#8216;this->begin&#8217; instead
../include/EST_TIterator.h: In instantiation of &#8216;EST_TRwStructIterator<Container, IPointer, Entry>::EST_TRwStructIterator(Container&) [with Container = EST_THash<EST_String, EST_Regex*>; IPointer = EST_THash<EST_String, EST_Regex*>::IPointer_s; Entry = EST_Hash_Pair<EST_String, EST_Regex*>]&#8217;:
siod.cc:47:3:   required from here
../include/EST_TIterator.h:292:17: error: &#8216;begin&#8217; was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
     { begin(over); }
                 ^
../include/EST_TIterator.h:292:17: note: declarations in dependent base &#8216;EST_TRwIterator<EST_THash<EST_String, EST_Regex*>, EST_THash<EST_String, EST_Regex*>::IPointer_s, EST_Hash_Pair<EST_String, EST_Regex*> >&#8217; are not found by unqualified lookup
../include/EST_TIterator.h:292:17: note: use &#8216;this->begin&#8217; instead
make[1]: *** [siod.o] Erreur 1
make: *** [siod] Erreur 2

```

Could you help me guys please ? :)

---

