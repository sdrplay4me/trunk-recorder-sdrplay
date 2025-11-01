# Preamble:
This project was developed on Debian 12 amd64.

### Add **contrib** and **non-free** repos to apt sources and update.

### Install required apps
```
sudo apt-get install -y apt-transport-https build-essential ca-certificates fdkaac git gnupg gnuradio gnuradio-dev \
						gr-osmosdr libuhd-dev libboost-all-dev libcurl4-openssl-dev libgmp-dev libhackrf-dev \
						liborc-0.4-dev libpthread-stubs0-dev libssl-dev libuhd-dev libusb-dev pkg-config \
						software-properties-common cmake libsndfile1-dev sox
```

### Install SDRPlay API
```
cd ~
wget https://www.sdrplay.com/software/SDRplay_RSP_API-Linux-3.15.2.run
sudo bash SDRplay_RSP_API-Linux-3.15.2.run
sudo systemctl status sdrplay.service
```

### Install gr-osmosdr
```
cd ~
git clone https://gitea.osmocom.org/sdr/gr-osmosdr.git
cd gr-osmosdr/
mkdir build
cd build/
cmake -DENABLE_NONFREE=TRUE ../
make -j
sudo make install
sudo ldconfig
```

### Install SoapySDR
```
cd ~
git clone https://github.com/pothosware/SoapySDR.git
cd SoapySDR
mkdir build
cd build
cmake ..
make -j`nproc`
sudo make install -j`nproc`
sudo ldconfig #needed on debian systems
SoapySDRUtil --info
```

### Install SoapySDRPlay
```
cd ~
git clone https://github.com/pothosware/SoapySDRPlay.git
cd SoapySDRPlay
mkdir build
cd build
cmake ..
make -j
sudo make install
```

### Install trunk-recorder
```
cd ~
mkdir trunk-build
git clone https://github.com/TrunkRecorder/trunk-recorder.git
cd trunk-build
cmake ../trunk-recorder
make -j
sudo make install
```
