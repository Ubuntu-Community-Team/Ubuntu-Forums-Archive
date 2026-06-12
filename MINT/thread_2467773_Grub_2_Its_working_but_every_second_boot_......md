---
title: "Grub 2 Its working but every second boot ....."
date: 2021-10-07
forum: MINT
---

### Post by znamloot on 2021-10-07
All,
I am a convert from the Windows (ewwww) domain and I have been using Linux for about a year.

I have a quadruple boot set up with:
Windows 10
Linux Mint 20.2
Zorin 16
elementary OS 6

All functioning and all menu items in grub work.

But about every second boot (first run or restart from another distro) I get the Grub stock menu instead of my proper menu. 

[INDENT][B]"GNU GRUB Menu 2.0.4
Minimal Bash like line editing is supported
blah blah blah

grub>"[/B][/INDENT]

If I type "exit" at the grub prompt it takes me to my menu?!?!?!?!?

Anybody seen this before or know how to fix it???

I have added my grub.cfg file (Grub 2.04) if that helps.

I cant see any errors in the script......

Any help would be appreciated. It's not the end of the world but damn aggravating.....](*,)

Thanks in advance

Znamloot

---

### Post by oldfred on 2021-10-07
Moved to Mint sub-forum, since not official flavor of Ubuntu.

I actually just had that. 
But after booting checked all my settings & reinstalled grub.
I have main working install of Kubuntu 20.04, but install each release as a test or reinstall to experiment with settings. 
Those installs overwrite my main installs UEFI & /EFI/ubuntu settings & I have to revert them. I used to backup ESP (still do), but found manually editing settings or just total reinstall of grub to be easier.
Sometime UEFI goes to an install that no longer exist as I have not yet housecleaned or installed over an old one changing GUIDs & UUIDs.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by znamloot on 2021-10-07
ok ran the boot-info summary report. (I had no idea it was available as a downloadable program - thx)
Link:
[https://paste2.org/](https://paste2.org/)

I await you verdict - thanks
Znamloot

---

### Post by znamloot on 2021-10-07
A quick note on this process. I ran the boot-repair boot-info summary report and directly uploaded it to [https://paste2.org/](https://paste2.org/) but how do you tell where it is?

Sorry, full of questions today. :confused:

Thanks again

Znamloot

---

### Post by ajgreeny on 2021-10-08
Please use the **pastebin** link you get in the boot-info report, **not** the one you have now tried twice without success.

---

### Post by znamloot on 2021-10-08
I have been through this several times and this is the "boot repair" screen after uploading to pastebin:

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAeYAAADwCAIAAABaCVCqAAAgAElEQVR4Ae2d 18T17r/9x/R323r3q99Ws9x233O Z7JkBgRIYEoBESUFrWiIKJSWq1XKmqhRSuoaKkXxBbxThXvjQIqIpdASGCSENmt9bbdrW1ta223iuL3NZPMZCaZCZOQQMDPvHyZmclaz3rW 1nzYWXN5Mmf7t // OPP967d  77767e/funTt3bt  fevWrZs3b95gt2 xgUBYEmhqauro6LDZbP/4xz   eabsPQRToGAXAKs4t64efPmrVu3bt  fefOnbt373733Xf37t378ccf79 //6fvv// 7t27t2/fvnHjxvXr17/  uuenp5r1645HI7u7m47s9mwgUBYEqirq7t69Wp7e/uRQ1UURTl9rD68n3MW 2AyjMaAU2 7u7uPHT147dq1np6er7/  lRN9Y0bN27fvn337t1aw k/3bp16/r16z09Pd3d3VartbOz02w2m0ym9vZ2o9HYymwt2EAgLAmcOHHCYDBcvHixsbGxqakpLH2EUyAgl4BTb41GY3t7u8lkMpvNnZ2dVqu1u7u7p6fn vXrt27d lNPT4/dbu/s7DSZTK2trU1NTVeuXLl06VJ9fX1dXV1tbe0FZjuPDQTCj8D /furq6tPnjx59uxZg8EQfg7CIxCQS8CptLW1tXV1dfX19ZcuXbpy5UpTU1Nra6vJZOrs7LTb7T09PX96CRsIgAAIgMAwIUBL9ihsIAACIAACYU/gpZdegmSHfZTgIAiAAAgwBCDZGAggAAIgMGwIQLKHTajgKAiAAAhAsjEGQAAEQGDYEIBkD5tQwVEQAAEQgGRjDIAACIDAsCEAyR42oYKjIAACIADJxhgAARAAgWFDAJI9bEIFR0EABEBgKCX7lVdeGfwAvPy3eQdv/nrj4LxxLw9 42gRBEDgxSLw/PlzqQ77eEuqyqhRo/yR7NHajxrv/Pzv3md9z3p// lmV/2 /OS/v rDuPRb/5l5 PYv1/ckj/YuMlr3SfuPfzzt6 t7 vjhjzc7675YM 2/A2vF2/ioUS//16y93Xe7K2aNhWSL8cE5EACB4BIQlWbRk3La9Uuyp5bfetr7zfH17727ZFXR3iv/fPLst4aVZABT5Zf/tqT 8dPb4pLNtHLjdNHy91fkF 9v Vdv3x8dH08KnmjLwYIyIAACIBA0Ah4C7XHoVzN S/aT1rUKRqRfHvte3eO X6rn/IVp8NX/fXPDScs/f3v8 MGdjuMfTWcnxqLnGcl 7toenc/9T57Po2nJftL2ocr5p C/3rvwqO9xw8r/YSbFr/6/tE9OmW/e/ OPn75pKM9WO9sePaWgtuvbew8e9fb 8dM3Vw/kJfyNKf3y3zL2dd 9//Dxkz9 7LlUNpegdf/Pbx 5/ z3k/PpqqM1K4 1OO7 8u/eJ7/fayqIwd8FXiCwCwIgEDwCnExzO4HZ9l yjYVRY17/zzfU09ad/1fvg4aVEbS0jo752PTw2QPbl5vyPig56Xj47GHrhxNHS55nJPvZjxc2ZGVkZMxNIPjrI4xk95o3xo7723 TmllFdd8/fXq36q2/Mgpb1PH7059a96zOWba94bveR9aSWLrqX Z  eDZo879eUuXr/us9sajZ780rB5Py 9ozcKi/KWLFy8rMdzsfXa/JnOMULKdFbv2r1m6dNWH78S/HhhD1AIBEACB/gk4J6n9l/NZwm/JZufGz58/73v8zYGM/6M10ymzlqKJzDR1dOyW7t7er8viR0ud73dhhGul7 mvPWeLpr1Bz5pHTy2/ bTX/PEEupVXyHWtT3rtJZpXXZL927F5zJz7L/od3/T22pg3uK6/EkGXthbHvCqYZTOSzVbkCmMHBEAABIJPYGgku9e2J2ta8rTpaVmrK4w/PXty7dOEP4/668Iz/ 57eNypmaNG/cfCs4/6aCWUOt vZPc6Khenpq05dffp07vHs5yLIs5W vqesltf37Pv9r35Zw/JHvX6O cfPfvp0Kw/j/rLhOydF7pu/vDrw19 vP97X2/3Fu1oSHbwRyIsggAI9EeAWw/hdvqrIf6 37Nsbi171Kj/mH/yt74nV/P 75XRSbtvPO3t3BDlmmVv7e7t/cf2yaOlzo8aQ8vqDwfS/uztFTMzd65lv/xGxpd3nz7917H5f2dm2dM/v/u0t/PTNE2Ma4uO/N/XXvaQ7NGazfbe3p5tuj /8V7tw6c/Xf7k7XiNZsbWjieQbG/aOAMCIBB6Ah4y7XHoV/t S3bv11 uzVm0 N0VBbvrvv1332P75jh6zTr6o/aHzx5Yqz9ZnVd8wvHw2W t6yJf9XE vuyb3mf3rpStWrqyYEUKs 7h8psn2aNGvfJ/752//6z3ekXKa/SadXxp96NnP3d9uWXtiveXf1C0 T0dswpOr2/09d64sH3t8pVFhzt/ffbYtjlu9Mt/X1r/x7Ofm8tyZqW uaC8qxeS7dfQQGEQAIFgEBAVaNGTclrzS7LjNll 7X3W97yv7 mT33 6bb18oPAt9tbhq/ TWnSq8 7DJ49/u2up Sjl765n/yTOv/z3tNLL139 3Pvkwe3L6zW8 48CyaZvYG60POr7/eoHztucxKziU5Y7vzDPhtzs2DOXEXunZH/39bXvHz5 dP96w56FE5hl7b9q3j9kvPnzo6fPeh/99sMt6/GlqlewMCJnWKAMCIBAUAj4kGYfb/lo2h/J9mFmaN/CXcSh5Y/WQQAEBosAJHuwSKMdEAABEBgwgREh2QOmAAMgAAIgMCwIQLKHRZjgJAiAAAjQBCDZGAcgAAIgMGwIQLKHTajgKAiAAAhAsjEGQAAEQGDYEIBkD5tQwVEQAAEQgGRjDIAACIDAsCEAyR42oYKjIAACIOCSbAIbCIAACIBA2BOAZId9iOAgCIAACLAEINksCbyCAAiAQNgTgGSHfYjgIAiAAAiwBCDZLAm8ggAIgEDYE4Bkh32I4CAIgAAIsAQg2SwJvIIACIBA2BOAZId9iOAgCIAACLAEINksCbyCAAiAQNgTgGSHfYjgIAiAAAiwBCDZLAm8ggAIgEDYE4Bkh32I4CAIgAAIsAQg2SwJvIIACIBA2BOAZId9iOAgCIAACLAEINksCfFXlSYpVR tEH8TZ4eegEI1SaeNDFGA NHn7w99t HBC0sgxJJNKtX6edHzS JWfBlf2JxY0p1Y m1i6fXEku4phU1xK76Mnl iTphLkMowDYByfrnJVJ4ZRu4pJi3e22Lcl6uhVYpUqcgwJRdCt/i9Vmbsauv8ItvvACn17 043WSxO zmE2uTJCDyo8/fD6hvgsAFZAGVQIAgiFBJtiouVfNOReJmR9L2W/3 S9zs0L5ToYqdMWQhIZMLzli6HdeuXXPYO42Xz 7fsnT6RAVBDPhCDX6PlPqcDRtypyoJ9eJK85XSmRHBbyKcLXr0OjDJVmiXV3e2VC1P0UyM0mqjJBRbEP2BjwQucAHjVaZ/ZrQeWRrFfaYg39x82XoiT0cS3AB2OGyW1osn9hZlxdN/x8jUkkvWU/mTpboYsC oOFQEgi/ZytgZulUn 5VpkQLbbsatrFHFTh8CFszIPluYEh0VrY1PmZdXcYnqOLhESw78Qg1dZ9S5B6jGF0 yhb0OTLKV6WWtXZWLVP0Ehx99/n4/1UL2ti/JpqWZHcDTM9dWNVqvbJ jhmSHLBhDZjiYkq2IGK9ZtCNp2w0ROZYx13bV2vZtzMIyRUR/l1NwiXlMRsi4vBqbaXemUnihktp5RVWGq2aKaq8/vDFDS09dlG XGFosdkd3V6vhiw9SJzDrFVMWlR5vMNu6rebmrzbNZj61i9V19kGdVWHqOvQeM3ciY1fXUHUbU5hJkSpjl9G0NzsyecXnZxqMXXaH3VJXPFPNLgWocw/Yepybo56uIt0E3RCpmVNQaWjpstvMDTVl709TM62TKfkHzze2ddocDltHQ832HGZuxocr1kHufTLlg4OGxnbaN8pYd2RrbpLTrDgWqcJinpPCXnOfJTx6PT5jV1u3qanRRNmtQv990aCF3uFEd81SsUApAYcfff6 OMz 4hjFBk6aORk9e93es8x6DWVqqj26PlUwO 5Pst2zaXLqRwZbw5a0CI B7Yx5Qt6xduP pbEC41xMsRPeBIIm2croxCkfNgxIrHmyHv9hgzJaP3joeCNbERGlzyo5a6FO5ccLZtlk4rrTluZDH8zUaeIzNp4ym6pyoxWEYpJ emJcdHRc6qr9LbZzH pJQplZ3t5RnZ8SEzlRk5AcTy wiNd19k8R9d4hS uOdFrZJyyuNDtsx1Zq6TozNtV3HlkarcrY1UZV5yVpozW6eI2am1cys xtcyaoVCqlklT4aoIgSH3 SYvxy8J5iXG66e UXehqrsieRK/80MaPrNJrtbrEeUU1HZYjy i2eZtIB93vMtWP5k3VxeqmpudVNlDN5VnM3x6xWlKFRT1nCrt7zTXp0Wum2LF1MyZrtQnphcdNrP iNjkjdK3OypyJDLoIUhIO704GX7LFy8uJI7PszvgswpzU59VYTDUbs5LjNNrEFQfNlr3CRXqZkq0Yr0vfdKbLbijUk7yBzfVeEZNZfLDqo7fpgYlt2BEIjmSP172lL7YGS6 ddvQldtXkWYMElB7ZDoedoihrt8NhN9UdKc6eohSsZZMzPqm3nl2vd05NVPPLTea92eN5/tFXYseeLCURMXt7E1X3WU7yRHYa47uuQrvyy66LxakkoUz/7GrdhXpTVc5Egoxfd7arJk9HMvrivsPGHQoXRnw3QU7nO0 Mz9jZSh1dFqNgJJu7fadeVGlp35UhdS P66C705wzzKkJCyraqMNL6D8F7s1dS6KwuOfCwm5zwl5L S9uk7MiNC4NR1yypcrLjaOgdTdzMmVjndVQ4LoXqszY1e6nZDu6KXNHh7nL5rjW4 i8UJoRrcDCCBfzEbMTBMlW6dISt/QEV6 d1hI3X1Pp3hoM1sxkxPDJ2/r4yXHRau5TOP8GlDKrwuxwdNvZrdtBHV0WHaFbsOmQ4aqpk6JMJoud ZRNKCYkL9l69JK5q/l0 ZqZ0SQhXpdTNlKXV0MZCpNUaVsunf5w3rpTLeXz1bGrjneeXhtPClXJOS9mRFYoXr6boN/tqlzIijGZsP6stXbDNA/jEellLV2Vi9hSDHhSrINcSATqQ5CJhQbr Y SSUK0lkRhcc/pzxbc3xKuPYIQ9loIx 2/uE0OuNATaTjiki1ZXmYcBa0LfXbHSEyyI aUtVirl7mfOY1I29porcmLJZ3SfG5Dmi5Ol5pf3d5cke28SSk2y bRxO7wIzBQyVZGJ o3 Te/Tvns9sXuh/9 0nf93uNFVXd9a72 2BoxKSHkXKVGNu/jMJla0kDVrBIuG0TmVJpNR9ZMn6QkFOqMnc1memHUtSnUCdmlhq62PVlq0bpsOXqdWZdX03muMLekzlCUrEwq Kpp59K8avOp/CkkT6OdFbgLfnxOFdVSlu76  K7CXLGpovWs sTXNN 1dwdLVS11yw7Yk5Zs4dk  ogvZIvEFbV3B2tFC0p4rUkCot7LizsZiXstdABt//iNjkrQuPScMQlW7K8zDgKWnf7HJG25Yr1VL7OGSMxySb1BV/ZGktnskNMoVleTZkrstXCJ0NI3fuHjJd3ZtKiLTWwORTYGW4EBiTZighVAOvXB1t/ec5urd/84Vuyk7bfmvLhFUUEfwUiBIylRjZ9QVGnC1LoJY6IlI8NXU0H12Yk6zQxsfrUGVPUROQ7VRbTkfxUbeR4VWTGDqdkk9qUmcmxE9XqKP37 4zMnUWxuvxuME ddZjaLtAzXzKp0GAymSw1q5nLV3CF81SS9tl28bNsvTYuMTUpRiXinrsJMnHtaYuxumCuPlaXkrPd0NlSkU3P1gTG3fLBVRTtIPcuU91WW/ZOml6nS1m09ZylvepdjUIci1RhUbBCx9wNMhrE6zV9 5GbjPP89w1c0Gv6ToM4HEH0eSNBqjxByIqjoHWez6q0zZdsTQfXzJ6i0SbN23iK8lwYIcj41cfMVF356nnTk5LTFhVVt9qvfJpO3/EVDmAyPq/GfHVXZpSCOc/MvuOcW wkNRmTWXxgX FsrGXzxtXw2R2QZNPPh/DuGcrc7/nuMavYz7 591hOrZjsT0OLVDjieW2Nn7H2cENHg/NZOjIus6jK0Ew/H0K1X65aoScJVdLSnacbzTaHo5uyGK c2TAzQjFx/rZaI9XtcNjMjad3LU9mHqIQqctrhlBELa402V0rmWTCujM283767qbXTJanZaR2Qemppk67g2qv3ZYxgfDdBKlJL9hnaKXsNnPjiR3LUphnW3jWCILgyQfnm0gHufecim9vOn uyWLvploNlWtnOheyRWvRUiVWmBDzXKBrvBYJYa 5xzDoIgL/fdHwMi4Oh BHn79PSJQnZMVR0LrAZ3XykrKaS0bKThlra69S7bu9vsRFRs/M33OqscPWbe9qrT1YvCjB WiV5wBWvllcb728JU1N36RxPVfEvNgOL5nEPDFyYAmeGOGPq2GzH7hkK7UpSdu lSO4HmXab/zBSfYR468e74ofbvt2KL9oM2yiOeiOCtSnv9b9KtyfsZH4fkR0vF6niYqMjNJNz911sePw 8JluJHYZ/TJXwKBS3aA35fZfivnwL u33v84N/PTnc mFZ2W1yjvSbvupU1/vYN5UNOwC8V9qtwyF0PvwbIhGWVdc1min4Av8lQtSEzjn3iKPx8hUdDRiBAyVbFpcqU2qAV23ZTOYTfaB yAKFhEAABEHATCFCyNe9UBE2LvSbUUpY1OeVux7EHAiAAAi8egYAkm1TKzPckJb6BndeX2BVhm/PvxRs66DEIgMDgEwhEstX6eYFprrPWvL3/3H35/oLKfp7IFm1CHT8nNIxCmnZZzGVSl7GmMCeZfcTW41CsxjA7N/J6NMwCAHdHJoFAJDt6fomonvZ7cnb5nZqOB496 54/f/6vX3qnyl4S4SxHZxaHJA4 7ozxszPTD8AGJ0U1mVx0ocv14DVtVXgYeB D5F7gDrA1g9Yj1iBeQQAEAsyXHbfiGKeh8ndKDD/  scz7vG 58 fz9p9R351Z8m45dUhCZuUZHtkZ/Y4DNwVOuWTpXo58zsFtGILDwO1K8e9iLiMworTVzqsdqqtvnrLwinub cH2qxYvSD1SMw0zoHAi0wgkFl2fGGzX1L71s7bl6/9zhfr58 f//DgqV9GnIWnFFwNSbQkJVuYndkjwUXArijTtlw2H1rCJovwOAzYrAz3FFEZxXtLl6cnT55MfwmSshxeyv7dCLhZkYrB6pGIaZwCgReaQCCSrS xy1fbJYf 9c fe7//tXdv488/PXzKCXed/aF8I1xJ/SZrSMJFS7ZY2mWP7MwThCmqlRIJoEnPfNmkMEOx8u1Pr5r25TgT99Apt9lD/9JPe7ZCp0zyK4M2nRzqUokwJzM95xfPrO2ZwNpHcmd3j0ISLRgFgReXQCCSnVh6ndPQfnd6vnt8pO3XGTvor8zc/OkJJ9klhh/7rStSoPR6SGJFSzYlknaZmbe6c1J7HDK1vLNFe fLFmYoVmfsbGnbmx3p6gnvUMIgITMrt4d7vnNGE2TCBzWWq2VMigoeVPFk0M7vpvPSdvtK7szrEc8wdkEABAZOIOSSnfyp67cfZ5Xf6aPvO9Jb3/Pnc/b4vZBNK3gIJZvLLuROYeyZ6tNj5YFWWK4WwWWL9s6XLYjThAUVRmP5fNfPt9DVuEMJg/zqdBGJrNwe3vrMGU1qsz6r66gtTWen mwbUsmghdlICF/Jnfk9Ys3iFQRAICgEApFsvxZGuJly0ZkfXIL9/Pn1H55w5/3a0ReHbmGEE193CmMPEfQ8FCqsO1u0V75sfqgmLq40Ne Yy6YmFBxKGRRNP 3divAvinTOaFK3aPclU 32 cxPofGdI5jU3u6szYREZm2PYoJMoYIeCY3jCARAYIAEApFsf28/OkX5pPkBJ9k1HQ/8Umqu8KDcfuQlV/PIzuxxKFRYLlu0KyS8fNnuICkmvXvA3LjN XuQ9IKH4FDCoHj6aadRfitC9yRyRisiZxdf6KjbnhEjmsFCMhm00DfJ5M4ePXL3HHsgAAJBIBCIZMct/5LTUPk7X3/vzrm6/uQ9 RX5JeOWHQ1Cp71NCPSIJ9l0Tktedmal8JBO1iySLdo7XzaXoZjULDtiubwlzfVknUJ4yCw iBgUTVrt3QqTHJnnrWgGbXJqgYEybEiNVDk3 mcjCYKgV9udOZSlkkELEBGERHJnzx55o8YZEACBARAIRLID CrNWztvP2WfyX7ytC VuRvJ12KZ 9EZmwbQWemqAj3iSbZHduYJ3smavRNAi TLdj4xcmBJ3ORVx7vqP5numt ScYJDv9JPi7RCeHorkodaEb2s2s7Pn xooH90kmA9pHMoiyeDFiCiSYold/bqkTRyvAMCIBAAgUAkW50wV6bCcsXWn7zHrYp03vo3d97fnfHxbwfQyVBV8VKxfhoip Sfoi4UJbOKLTz0/jWDfswN7dtiyZ09Oji0DqJ1EBiJBAKRbIJUJpZ0 6W2R4y/cpJd1fyLX3W5wvpim4IMzZf1Agutn5JN6j88R50rcP1GO FxSLvgp8HAvA5OLbHkziI9Ck5jsAICIOAiEJBkE4TWz Sr1J1HnGR/cOx7ToX92tEs3o24gQAIgMCLTCBAyVbFzkjadlOm4E4ru/3oieuR7KfPnr 5k/5azYqj3112/O5HZqhtN/FbYi/ySEXfQQAEAkwL5QSnW3VCpmQvP/odN8V 3NtXdPaHC7aHz/qenzA/mFbm qJNv6biVhxDwEAABEDgBScQ4CybXnfVTksslfVzvZ83/sxJtnPnh9 erjnuz/II/XO901/wUKH7IAACIBC4ZBMEEbOwrN/ZcdL2W19cdUv202d9pywP3trl37fVY7K3I1QgAAIgAAIDkmyCVE5Zf7lf1Z61 479n4/ eNJnsP6W9YXfP0Yz5cMrigj2 92IGAiAAAi8wAQGJtkEoYzW64ut/ap2wAX0myhldMILHCB0HQRAAATcBAYq2QRBqHRvJW6 FrAo 6iYuPnaeN1bbmexBwIgAAIvNoEgSDZBEON1b k3UT7EN4C39MU21eRZL3Z00HsQAAEQEBAIjmTTD5BE66d82BCANItWmbL MtZDBIHCAQiAAAgQRNAkm84GF6GKyf40aZusJ/9ElTpp 63E0m/p50NIJaIDAiAAAiDgQSCYku00rdSm6FbWyP9upFu7t92MW3FcpZ3m4SIOQQAEQAAEnASCL9lOu8rYGZqccpm/X6MvtmkW78b30TEoQQAEQMA3gVBJtrNVBalUx8 JziyOW3Z0SsFVfbEtsfR6Yul1fbEtvuBq3LKj0ZnF4 PfDq/8fL6B4V0QAAEQGDoCoZXsoesXWgYBEACBEUgAkj0Cg4ougQAIjFQCkOyRGln0CwRAYAQSgGSPwKCiSyAAAiOVACR7pEYW/QIBEBiBBCDZIzCo6BIIgMBIJQDJHqmRRb9AAARGIAFI9ggMKroEAiAwUglAskdqZNEvEACBEUgAkj0Cg4ougQAIjFQCkOyRGln0CwRAYAQSgGSPwKCiSyAAAiOVACR7pEYW/QIBEBiBBCDZIzCo6BIIgMBIJQDJHqmRRb9AAARGIAFI9ggMKroEAiAwUglAskdqZNEvEACBEUgAkj0Cg4ougQAIjFQCkOyRGln0CwRAYAQSgGSPwKCO0C4plBO1mgmKEdo7P7tFqmM0UUo/Kw24uEI1SaeNRAi8Qao0San66MEgA8n2pk8o9e/tON1ksTvs5hNrk0iREi/MKcWkxXtbjPtyNQMcjEGwo8zY1db5RXYwZIpUqbyiGgQPBzAq/GydjF93hjqzNp4k/KzIuCjWfUnf YUlQhCID5Lt fMG3zd/6gW/rHJ uclUnhmMwdmfc5BshhCZWnLJeip/Mn0hK7TLqztbqpanaCZGabVRXtd2f0hH1vtKfc6GDblTBzwWB25HQi/8xq1eXGm UjozwrPiwD30tOjPsX tk/Hrzjolm/CvIkFIdV/UWY/CUiGQ44My/TOj9cjSKO5vP/nm5svWE3k6kiCTC85Yuh3XrjkcNkvrxRN7i7Li6QHHvyq93fPwzbvAYJ6BZA8mbbot/uBQppe1dlUuUg22D2jPNwEpvfBdy/tdde4BqlFEsr1Lhu8ZnmT766Rf3fcoPJAQ JJsesJ0tjAlOipaGz89c21Vo/XK9jlqwVXp3U0P37wLDOYZSPZg0qbbEkh2xq42Rw zXbNULHDNL9VZFe2dB991ThIUUe8dsjSXpTNTAc2cgkpDS5fdZm6oKXt/mprxXTCelIsqu5rL5gjndcq3SwwtFruju6vV8MUHqcwaLZm84vMzDcYuu8NuqSueGUGQ2nlFVYarZopqrz 8MUMrnPJ7vUvG5lYZTUeW058WFNHZe5taq96NJQky5YODhsZ22ixlrDuyNTfJ6SQhZt/DB7V7OcKrOYIgU/IPnm9s67Q5HLaOhprtOczsiCEa8/b6z881W x2qq2 LDtKxdrxUSV69rq9Z5kFKcrUVHt0faqgu7Re2JvOn7tqsds7m89V5KexMzZSNAQEIX5enXvA5gxvj6N YwrXBqdH5JRFpccbzLZuq7n5q02zlQThfUY6vmKUvAx6j29365JIlfELNx 92G61U20Xz9a325iFEYKrSBCkB3OF2Bjz6r6Iw5x7HoXHZ xq6zY1NZoou5Ufbs4Hb1Ccqf4k2/UZl74Yp35ksDVsSYvgX5WcHW7HwzdSItxceb uAqnBI2VEKNm kHL BLqDhRGGHH9wMOOvMmeiSqVSKiO4KzpyUWWHqXLxRLr8 PnlbaaKbDVBkPr8kxbjl4XzEuN0098pu9DVXJE9SUEQ0pc0GynFJP30xLjo6CBh SQAABZ3SURBVLjUVftbbOc 1JMEc/lR1XlJ2miNLl6jJhPXnbY0H/pgpk4Tn7HxlNlUlcu7wSH6rkKT80WzqXplvHbR3ubmyhxG5OkeUUfzpupidVPT8yobqObyLFruRC0whd0 uK9GMWeYwkdW6bVaXeK8opoOy5FlWvqTrwvLx/OTdVpdUmpiNMnZka6SV2Mx1WzMSo7TaBNXHDRb9grXremKttqy3JmJusnTc0rPWdqqmCV2qRBInWdCs23OBCa JPc5ndM ZWZ5e0d1fkpM5ERNQnL8RAXhfUYyvmJIVV4G2THAe 2XT8T0DReo5oNr0/WxuqT0/IPNnpLtzZwQG2Me3Rdz2M3EozATu2PrZkzWahPSC4 b2HCzzouA4rooU7IV43Xpm8502Q2FepJ/VXJ2uB0P36TCzZVnnJd7FUhZkzLCl2zfSDl/At2BZDPk IODHX eSNVZ5caOfTlRCiJiZmljx76ciQRBTv k3np2PS239DY Y2crdXRZjELykvY0Sh/TDXbsyVI699x32MgZfOOq eUm897s8awFqXcV0dl7msyNjcamioUxzotP2KMJCyraqMNLJinELQgLc0Imo7B6UaWlfVcGPStlsKyL5/7e8bomsM rkrKxzmoocN3sVWbsaheTbDcc1dwdrVT1smiFVAikzgtDw9J0hYG2HzF7exNV91lO8kTWfe8zQiPuT1GilCK9DPJaZXc5LNwO/Q6PT2pxg/X02ilOn3gLI2x5EeasbcEYY5SOWxcSdZgbY8Ju8oIo9I0bJCKgOB/6kWxHN2Xu6DB32RzXehydF0ozohWCz76cHW7HoyNSVyJXngXlPOH7KpggZU3CCMGT7H6Qcv4EugPJZsjJkWxCOav0iuXoMq0ytbi oyqXnqcqsyrMXZUL2ZtzZML6s9baDdNI4Vh3X9LuMJG6BZsOGa6aOinKZLLYnSswwgFBG3c4uu3s1u2gji7jptnS76rTy5ocDpNzDkq3KDRLJhYarOc/SibFLXArGE5f2boyCkekl7V0VS6i//QIsQh8YA0y5qWq9C/Zgl6IhcDDB4nQODvJ/M85ppiQvGTr0UvmrubT5WtmRtOLTF5nBHrhjq84JdKrOq9Z1y7XOrdDvyHFR0SyPfpL1xYdYwLPmUhJjzHhMPYYSG7f3APMGxTX04g5ZS1W m8seyYibWujtSaPXrij17LPbUjTxelS86vbmyuynUte/KuSreV 9e6I2DBwlxeAJQTjx4tArHAAuwePhBG ZIuPAa7bbocC3INkM D4g0MYFT5XMmHtaYuhaMnm rYvFjErJOSMTRetZ9cnuOZjqrk7WqhqepatzNpr7qhwzYndlzRnLTKn0mw6smb6JCWhUGfsbDYzi bCpsnUkgaqZhWz0sBV5Hak3p0we2ud8XhJSXW7kVnI9pJs9/xU1L7QB 5qFG9OUDhiTlmzU7LpwlbnUivrL1eS26HfcVeJSNtyxXoqX ck2b9kq7P2tFFHlkYrpEIgdZ4Yn1NFtZSlC 8seFEiFOqE7FJDV9ueLHbhn39GIr7ilJwM NVZKu5XDgu3I TDdOerAtfnORHJ9mYuPsaE3fflMP2xUchKwjdukLi6I9pTUl/wla2xdCY7vVFolldTZufqIu95LVL3/iHj5Z2ZzMId77ybFLsn9E0y3GxxDyd9XwWS1gQECM4IX7L7Qcr5E gOJJshJ0 yCcXErPIWiqKad2a4rmMyce1pi7G6YK4 VpeSs93Q2VKRTU8kSO2yo5aOmo/T9dromCkrj1Aetx8j36mymI7kp2ojx6siM3aISjYRkfKxoavp4NqMZJ0mJlafOmMKqx6006LvTnh726X26pVTSFK35GBb26Elca4lcltt2Ttpep0uZdHWc5b2qnfpB61FLQgHpXug91/Yrb9ERMpHBspYXZiZrNNop6SkTFZzZrkdpg cyhOqtM2XbE0H18yeotEmzdt4ihJbGKGO5Om1MVr97FWf0yvyC5wr8hIhkApNaskl28XPsvXauMTUpBh29YPrKalNmZkcO1GtjtK/v8/Ydei9qAivMwqp IpR8jaoUGbtMdv4T7xxrbt3PPiQSWtPWUwnSxam6DQaXfqWWvYhP/a rhdzregYo4c6r/sqn2PMozB9 5Fbm KFm42pSE Zy4v5j4xffcxM1ZWvnjc9KTltUVF1q/3Kp n0iOZffQRBxufVmK/uyoxSMOeZ2Xecc4udpHbPVj18U0qEm3OAdlL2VSB1XUsamVPWTJ0uSKEX08TGAOfFwHcg2c7hxPt7zo4/UbhkclGttW7jdPccjdSkF wztFJ2m7nxxI5lKezX8yKmLN5W02i2Oxx2 vmHA3nJnDjQllVJS3eebjTbHI5uymK8cmYD/aCwV9NkXGZRlaGZfrCEar9ctYJdNHf65vXu JQN582n1jpLkVNWfWluoT9k0mbpZy2aLPZuqtVQuXYmfYeU3rwskJ4 8FzqrzDvGqY/lNOet3TaHTbz1aMfJHFXO88gf5ZNL9wmLymruWSk7JSxtvYq1b5b M0EMiX/UG1zB9Xt6Kba6qtLec 9SIRAIjSkdkHpqaZOu4Nqr92WMcFJgoOvmjh/W62R6nY4bObG07uWJ6sVXmfoKlLx9aIUIVJd/c5 yrhjLjvj5M/xpfmQMbPXO5 ocdi72hrOfppN36vglfdkrhYbY4Rn970c5o9TYeEo35LtjY5l63wlo2fm7znV2GHrtne11h4sXpTgfJJWKNkEoXyzuN56eUuaOrXkkuvZLecjPrbDS5gPty5zHnGUCDfrAw1K9lVAPzEidl1LGhk/Y 3hho4G500Cn0hZfwJ9hWTLJBcxISpSHZ2cu/ti0xc57gU5mbWHthjvqh5aR3y2HhEdr9dpoiIjo3TTc3dd7Dj8vsSSkE8rw LNiLe2NBgrsiOHhbMjxcmgXAVBMTIwopBsefzIGUXnqW5r2/nK/LSJ7g9n8ioPdakwGGf9IyATllXWNZsp pn0JkPVhkx6SWeEbuqpiz9YPNX9SW2EdjO8uhWUqyAoRgbGBZI9MH6oDQIgAAKDSACSPYiw0RQIgAAIDIwAJHtg/FAbBEAABAaRACRbDuyA0wT7VXHwUu7K6fMwLAOAwyhoCFaAwYJkywAX8D0HvyryvvMqwycU8SIwKABHUi71wc9z7W5xUILlNURGwglItowo qW8fHt VQyHQUw/ISt4EtbO/4oxv2thuD8IAEdYLnU5ea6DG2iuxUEIVnA9DxtrkGwZofBLefn2/KoYDoOY VLD2Y9TtRp2m6gaNo80DgJA5FLnD  B7A9CsAbiXhjXhWTTX7vLqjDRX0ymxYmMXV1D1bnSKKsydhlNe7PpL32JpQmWSqrLxZuWbImK3omw YNYKi2vy3LQk3ezHnt D811XjzxtEdmbd5jxl75giUSeRNiCZ3ZhNr0Nz7baveVfLTtcG1Lp81mbqzZmk3nIJGCwwcomgqc7SUdZtEU22zT3um/XVXpgApyqUvYEeY9j T/qAIv4QzbnHRPfSXaltW0Kyjq7AqTZX u66uDqnk7jWY6E6V7SiEWCD4u7 Har/OiweVaFAaL1xR2 yEAyaZ/Ooz xYLWHcwvFkxYXGl22I6tpL95R87YVN95ZGk0ndyOEkkTLJVUl2NOD1DRiqK5p3k/H8dUFMnty1oOdvJu1q6oZEt1k3HSnVmbtSGehls0kbdoQmfabNehFVNiomOnLa1o7DYfK5yjj43VZ5VeoIy7MsYzQiOW/puvAr5zFvvskUj6b65rtG d7lzqPu24yQhyzvEku7 e ko/LbNpl eKqNz9FmN5JpOjJiJtS0Pn4aXRCp5ki2XW5notCrM/5wnJ4DJZSvjB4hrCjgwCkGwakkK78suui8WpJKFM/ xq3YV6U1XORIJOl9ZVk6dzp eny/JSGEsl1eW4M1c4 wuzvIqiibD5g1hQkeBy 3KGiRAl72bWsh3WTotzM9eVzIyQTDwtdJLzTSpfsEgib66OM1WGd9JwOm0JdSCXURr6x0qYVEjCdt1weAClfHA2KK9H7ni53RQ2Lc O9O9d8K2J9VQlnWhbbtOs64pJ7x00t yYq6KTMBVftBx5n84LxneALUmfcwaCPSMOk19XzHn d1fdNrlavGCx7eBVFgFINoOJ1OXVUIbCJFXalkunP5y37lRL Xx17KrjnafpX7Hmxhld1p0m2CNDsTupLkfeR0WvFL3R9G8YsD/SLKjozu3LGSaCm7ybs8vMsg0bZ8VPZjZdbJTSM/m1u5tCJzkb0vmCvRJ5iyZ05pul1YKqXs7kdCHj6Bh9NFX4F5QHh6cC0j7QbkoGjt80L9Bc14QjQaYdeZIt2lPp9NPyuuB2nFBE5VR1tOzMGB RWnKp48C7TGIwrr igWBri8Pk51UXdV7UJtciL1hsO3iVRQCS7cREa3bnucLckjpDUbIyqeCrpp1L86rNp/LpnwHhxhld1p2vTjKpLkdeqqJ4ompJyXan5eUsE0QQk3e7rYotjEh2U9A7gQ3RNN/eibzFEzrzzZIpG92SHZtXQ533kmw3HJ4K M5ZLK9H7kC7 8b3jVk4k8iWzs94R/ JEE ezrcm2lNnw2Lpp V1we04/fEwc3ersSIns7TBWLHAmZGKdUA8EGxtcZhsXbqUmPNRvjPC84LFtoNXWQQg2S5MzONbHaa2C/RvypBJhQaTyWSpWc2k3OePTp5kE1JJdTnyUhVFM oyny5dKXfpimK5fTnL9GrOQJN3K2Iyiw/sK5zNS3MlJtmS3RT0jueZaO/EEnn3nzRcTAuYWbYYHD5AUR84H6UCJ hR/5Itl4xUcm1 c2I9VXrn6favC1xpZkeZtvlyZ2uLqaF0livrK uAeCC42qIw2bp0KTHno0SzdXO1eMESGYdc09jxIgDJZpEoohZXmuyuXx8kE9adsZn3u34dlxtndFnBlSyeVJc1KTU9pwe5SCJsXspdukXx3L6cbdrIwJJ3kwl5x9qNB5bEupcdRSXbV 5gLuE93y/v3kkk8u43abiYFjCSLQqHB1CcsNtJ8cBJB9pVU1CAPifDDl1MPLk235pIT5MneWbudvsvv2leHTI /5TV5v6pUvf4FA0Ev6b3cO3H amkqE13LXewRMYhr2nsehCAZHsACY9D98gW9Wc4J 8W7ZBfJ/uB45ctFAaBYUYAkh2WAfOtSsM6effAefuGM3D7sAACYUwAkh3GwYFrIAACICAkAMkW8sARCIAACIQxAUh2GAcHroEACICAkAAkW8gDRyAAAiAQxgQg2WEcHLgGAiAAAkICkGwhDxyBAAiAQBgTgGSHcXDgGgiAAAgICUCyhTxwBAIgAAJhTACSHcbBgWsgAAIgICQAyRbywBEIgAAIhDEBSHYYBweugQAIgICQACRbyANHIAACIBDGBCDZYRwcuAYCIAACQgKQbCEPHIEACIBAGBOAZIdxcOAaCIAACAgJQLKFPHAEAiAAAmFMAJIdxsGBayAAAiAgJADJFvLAEQiAAAiEMQFIdhgHB66BAAiAgJAAJFvIA0cgAAIgEMYEINlhHBy4BgIgAAJCApBsIQ8cgQAIgEAYE4Bkh3Fw4BoIgAAICAlAsoU8cAQCIAACYUwAkh3GwYFrIAACICAkAMkW8sARCIAACIQxAUh2GAcHroEACICAkAAkW8gDRyAAAiAQxgQg2WEcHLgGAiAAAkICkGwhDxyBAAiAQBgTgGSHcXDgGgiAAAgICUCyhTxwBAIgAAJhTACSHcbBgWsgAAIgICQAyRbywBEIgAAIhDEBSHYYBweugQAIgICQACRbyANHIAACIBDGBCDZYRwcuAYCIAACQgKQbCEPHIEACIBAGBOAZIdxcOAaCIAACAgJQLKFPHAEAiAAAmFMAJIdxsGBayAAAiAgJADJFvLAEQiAAAiEMQFIdhgHB66BAAiAgJAAJFvIA0cgAAIgEMYEINlhHBy4BgIgAAJCApBsIQ8cgQAIgEAYE4Bkh3Fw4BoIgAAICAlAsoU8cAQCIAACYUwAkh3GwYFrIAACICAkAMkW8sARCIAACIQxAUh2GAcHroEACICAkAAkW8gDRyAAAiAQxgQg2WEcHLgGAiAAAkICkGwhDxyBAAiAQBgTgGSHcXDgGgiAAAgICUCyhTxwBAIgAAJhTACSHcbBgWsg8IIRGDdu3JgxY157kbYxY8aMGzdOfpwh2fJZoSQIgEAICYwbN27s2LGRkZExL9IWGRk5duxY aoNyQ7hEIRpEAAB QRef/31F02vnX bIiMjx4wZIxMUJFsmKBQDARAILYHXXnvtRZpeC/r62muvyYQLyZYJCsVAAARCSwCSLYcvJFsOJZQBARAIOQFIthzEkGw5lFAGBEAg5AQg2XIQQ7LlUEIZEACBkBOAZMtBDMmWQwllQAAEQk4Aki0HMSRbDiWUAQEQCDkBSLYcxJBsOZRQBgRAIOQEINlyEEOy5VBCGRAAgZATgGTLQQzJlkMJZUAABEJOAJItBzEkWw4llAEBEAg5gcGSbI1 7pod1bUtFmu3rdN48Xj5 vlJGua7iNp52xus5z6e4TyKTVtztNVyvnSB3nks LpikA/w7ceQDy80AAIgEFwCgyLZmoSFn9ZTlrrPC9 dl/Zm2tzcgopai7Vh9zuJmpgYnmTHvrn6QJO59tNF9PnQb5Ds4I4lWAMBEAg5gcGQbO3bm ttbfvfd02raS3W6JdUttobts L5SR7clrewaaO89sXDo5ex8TEQLJDPrzQAAiAQHAJDIJka2duqrUbyxfFCubNsQt3t9gvbnlby8yya/d Wt3S8dXW7EFYD HcgGQHdyzBGgiAQMgJDIJkx2btaLbVbpql5bSS3tGmfXKBEXJasrutFOXoMmxfOHVQVkRcjkCyQz680AAIgEBwCQyCZGvT p9ln9uQlbv1dLv1atXqN4WzcYHOB/cAkh3csQRrIAACIScwCJIdo52zpd7WdmA5bwqtSVy6zyhcy9bE6NLWHGqyNh9YNV04IQ uULutQbJDPrzQAAiAQHAJDIZkx2gSFpbRT4x88dG7GbPSZs7LLdhLPzFSnuvxxEhMTNys9cfaqbpPFyQMwgoJJDu4YwnWQAAEQk5gUCSbeUTE9Vy2rdveZbxUU74 U/S57BiNftGuBmtL5VLe8yXuiXFQ9yDZIR9eaAAEQCC4BAZLsoOqtUEyBskO7liCNRAAgZATgGTLQYwvrMuhhDIgAAIhJwDJloMYki2HEsqAAAiEnAAkWw5iSLYcSigDAiAQcgKQbDmIIdlyKKEMCIBAyAlAsuUghmTLoYQyIAACIScAyZaDGJIthxLKgAAIhJwAJFsOYki2HEooAwIgEHICkGw5iCHZciihDAiAQMgJvP7665GRkUH6bspwMhMZGTlmzBiZfCHZMkGhGAiAQGgJjBs3buzYsS aakdGRo4dO3bcuHEy4UKyZYJCMRAAgZATeOONN8aMGfPai7SNGTPmjTfekE8Wki2fFUqCAAiAwBATgGQPcQDQPAiAAAjIJwDJls8KJUEABEBgiAlAsoc4AGgeBEAABOQTgGTLZ4WSIAACIDDEBCDZQxwANA8CIAAC8glAsuWzQkkQAAEQGGICkOwhDgCaBwEQAAH5BCDZ8lmhJAiAAAgMMQFI9hAHAM2DAAiAgHwCL7300v8H0UvzdA0cfhsAAAAASUVORK5CYII=[/IMG]


There is no link..... at least in the above screen. Is it somewhere else? 

Really lost here - let me go back to the documentation. 

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

This screen looks nothing like the ones in the above link ....

Maybe I'll try the boot info ISO and see if that works.

Cheers

Znamloot

---

### Post by znamloot on 2021-10-08
Here's the screen - copy and paste doesn't work on this forum.

---

### Post by znamloot on 2021-10-08
Ok I got it to work from the boot-repair-disk-64bit.iso when I rebooted:

The link is as follows:

[http://paste.ubuntu.com/p/7r59QNk9hT](http://paste.ubuntu.com/p/7r59QNk9hT)

I hope I got it right.....

tested and it works.....

---

### Post by znamloot on 2021-10-08
I also ran it on Zorin 16 but got a different result - this time it shows up on the screen!

The link is:

[https://paste.ubuntu.com/p/J98CNXxyvQ/](https://paste.ubuntu.com/p/J98CNXxyvQ/)

---

### Post by oldfred on 2021-10-08
You have UEFI system, gpt partitioned drives & UEFI boot of every system.
But you have an old BIOS boot of Windows in nvme1n1. Not sure how you would have that as Windows only boots in UEFI mode from gpt drives.

But you ran Boot Repair in old BIOS/CSM/Legacy mode. Since UEFI system with UEFI installs, you never should boot in BIOS mode. That may try to do a BIOS type repair can cause further issues.
> The current session is in BIOS-compatibility mode.

Do not really know grub-customizer. It replaces grub scripts with its own proxy scripts.
Those with multiple installs & using grub would normally be better using grub and modifying it if desired.

Since not showing UEFI boot entries cannot tell if that is part of issue. It could just be UEFI set to boot an install that is not working, so then it boots second in UEFI boot menu. Or is trying to boot Windows BIOS boot loader, fails & then boots a valid entry.

Post this from UEFI boot in code tags to preserve formatting. Use # icon in Forum Go Advanced editor.
sudo efibootmgr -v

---

### Post by znamloot on 2021-10-08
This is it I hope (I am learning quite a bit with this):

[COLOR=#000000]sudo efibootmgr -v

[/COLOR][FONT=monospace]```
[COLOR=#000000]BootCurrent: 0000[/COLOR]
Timeout: 1 seconds
BootOrder: 0000,000D,0002,0001,000C,000E,000F,0010
Boot0000* ubuntu        HD(2,GPT,8e6b545c-1fa2-42a0-d5a7-31f8eefaf8ba,0xfa000,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* elementary OS 6 Odin  HD(1,GPT,838c823f-7454-469b-881b-6209caba2e0b,0x1000,0x838f7)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* Windows Boot Manager  HD(2,GPT,8e6b545c-1fa2-42a0-d5a7-31f8eefaf8ba,0xfa000,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.
a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot000C* Hard Drive    BBS(HD,,0x0)..GO..NO........q.S.a.m.s.u.n.g. .S.S.D. .9.7.0. .E.V.O. .5.0.0.G.B....................A...........................%8\..&......4..Gd-.;.A..MQ..L.S.4.6.6.N.X.0.K.C.2.8.3.5.9.H...
.....BO..NO........o.S.T.3.0.0.0.D.M.0.0.8.-.2.D.M.1.6.6....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .5.Z.5.0.V.F.F.Q........BO..NO........o.C.T.5.0.0.M.X.5.0.0.S.S.D.1.
...................A...........................>..Gd-.;.A..MQ..L.9.1.9.0.1.E.D.E.6.2.D.F. . . . . . . . ........BO
Boot000D* ubuntu        HD(1,GPT,9c538813-d40e-421f-855e-d3aedcf56afa,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot000E* UEFI: SMI USB DISK 1100, Partition 1  PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(1,0)/HD(1,MBR,0x38812088,0x800,0xe77800)..BO
Boot000F* UEFI: SMI USB DISK 1100, Partition 2  PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(1,0)/HD(2,MBR,0x38812088,0xe78000,0x10000)..BO
Boot0010* USB   BBS(HD,,0x0)..GO..NO........i.S.M.I. .U.S.B. .D.I.S.K. .1.1.0.0....................A.............................6..Gd-.;.A..MQ..L.C.C.Y.Y.M.M.D.D.L.U.Y.N.G.G.C.V........BO
```

The last 2 uploads of boot-info were created in my Zorin 16 OS if that makes a difference.....[/FONT]:confused:[FONT=monospace]

The boot-info app doesn't give me the pastebin url .... don't know why....[/FONT]:confused:

Thanks again

Cheers

Znamloot

---

### Post by oldfred on 2021-10-09
Zorin just may not have something Boot-Repair needs to upload. Or is Internet not working.

You show three FAT32 partition, one specifically labeled as ESP, but label does not matter, its whether is has esp,boot flags so UEFI can see it as an ESP. Report shows all three with esp flags.
You show three different ESP used for UEFI boot entries. I expect Mint  uses an Ubuntu entry even though not an official flavor of Ubuntu.

I do like to have an ESP on different drives, but Ubuntu makes it difficult to use that. Other distributions let you set which ESP to use during install.

First in Boot Order is 0000 an Ubuntu entry use the partUUID of nvme0n1p2 .
Second is 000D an Ubuntu entry using nvme1n1p1.

The grub.cfg in nvme0n1p1 has this which has correct UUID, but shows msdos1 and you only have gpt partitions.
I might just edit msdos to gpt and then see if it works.
search.fs_uuid 99149bfc-4662-45ec-b682-552cf640f5ca root hd2,msdos1 

You can see that comparing GUID/partUUID entries in efibootmgr & lsblk which also are in the report.
sudo efibootmgr -v
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

