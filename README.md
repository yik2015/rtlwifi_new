rtlwifi_new
===========

A repo for the newest Realtek rtlwifi codes.

This code will build on any kernel 3.0 and newer as long as the distro has not modified
any of the kernel APIs. It includes the following drivers:

rtl8192ce, rtl8192se, rtl8192de, rtl8188ee, rtl8192ee, rtl8723ae, rtl8723be, and rtl8821ae.

Added March 16, 2016: All branches of this repo now support the ant_sel module option
for rtl8723be. In addition, patches to implement this feature have been submitted
to the linux-wireless repo. If accepted, they should appear in kernel 4.7; however,
they will be packported to kernels 4.0 and newer when they reach mainline.

---
lspci -vnn 看网卡型号. 是Realtek 的 [10ec:b723].google一下，对应rtl8723be。

然后make 驱动

```shell
sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtl8723be
cd rtl8723be
make
sudo make install
sudo modprobe rtl8723be
```

结果编译错误，搜到[http://askubuntu.com/questions/428873/errors-running-make-on-wifi-kernel-module](http://askubuntu.com/questions/428873/errors-running-make-on-wifi-kernel-module)

说是kernel版本的问题。

The most recent version has been modified to correctly compile on kernel version 3.14; you are using 3.8.0-36. It is necessary to get an earlier version of the package. Please open a terminal and try:

```shell
cd rtl8723be
make clean
git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9
make
sudo make install
sudo modprobe rtl8723be
```

重启。OK
