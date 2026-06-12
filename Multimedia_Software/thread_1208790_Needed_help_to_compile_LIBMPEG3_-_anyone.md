---
title: "Needed help to compile LIBMPEG3 - anyone?"
date: 2009-07-09
forum: Multimedia Software
---

### Post by zolero on 2009-07-09
I'm trying to compile libmpeg3 (latest version 1.8 ) from author's original source. Also I was taken and adapted the patch from Debian Lenny upstream to get shared libraries too, and changed a52dec in the source tree to latest 0.7.4 version. Patches were integrating perfectly (attached to the thread, in case anyone want to give them a try), but code won't compile. Below is the output of make command:

```
root@bluestorm:/home/zolero/workdir/libmpeg3-1.8# ./configure --prefix=/usr
Configured successfully.  Type 'make' to build it.
root@bluestorm:/home/zolero/workdir/libmpeg3-1.8# make
gcc -c -D_REENTRANT `cat i386/c_flags`  audio/ac3.c -o i386/audio/ac3.o
gcc -c -D_REENTRANT `cat i386/c_flags`  audio/dct.c -o i386/audio/dct.o
gcc -c -D_REENTRANT `cat i386/c_flags`  audio/huffman.c -o i386/audio/huffman.o
gcc -c -D_REENTRANT `cat i386/c_flags`  audio/layer2.c -o i386/audio/layer2.o
gcc -c -D_REENTRANT `cat i386/c_flags`  audio/layer3.c -o i386/audio/layer3.o
audio/layer3.c: In function &#8216;mpeg3_layer_header&#8217;:
audio/layer3.c:1405: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_state&#8217;
audio/layer3.c:1407: error: &#8216;MPEG3_ID3_IDLE&#8217; undeclared (first use in this function)
audio/layer3.c:1407: error: (Each undeclared identifier is reported only once
audio/layer3.c:1407: error: for each function it appears in.)
audio/layer3.c:1413: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_state&#8217;
audio/layer3.c:1413: error: &#8216;MPEG3_ID3_HEADER&#8217; undeclared (first use in this function)
audio/layer3.c:1414: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_current_byte&#8217;
audio/layer3.c:1420: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_current_byte&#8217;
audio/layer3.c:1421: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_current_byte&#8217;
audio/layer3.c:1423: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_size&#8217;
audio/layer3.c:1427: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_current_byte&#8217;
audio/layer3.c:1428: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_state&#8217;
audio/layer3.c:1428: error: &#8216;MPEG3_ID3_SKIP&#8217; undeclared (first use in this function)
audio/layer3.c:1459: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_current_byte&#8217;
audio/layer3.c:1460: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_current_byte&#8217;
audio/layer3.c:1460: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_size&#8217;
audio/layer3.c:1461: error: &#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_state&#8217;
make: *** [i386/audio/layer3.o] Error 1
root@bluestorm:/home/zolero/workdir/libmpeg3-1.8#
```Does anyone know what a life can this weird **&#8216;mpeg3_layer_t&#8217; has no member named &#8216;id3_state&#8217;**  mean, and how to get rid of it? I've googled for an answer already, but nothing useful yet. Any advises will come in handy and I thank you for them in advance.

Zolero.

---

### Post by zolero on 2009-07-11
Unbelievable... Noone? Bump.

---

