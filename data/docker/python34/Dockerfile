FROM centos:6.6

ADD ./zhtsyw_init.zip /home/

ENV ZHTSYW_INIT /home/zhtsyw_init
ENV USERNAME sjdev

RUN set -ex \
    && yum install -y unzip tar gcc zlib zlib-devel \
    && cd /home \
    && unzip zhtsyw_init.zip \
    && rm -rf zhtsyw_init.zip \
    && useradd -b /home "$USERNAME" \
    && echo "$USERNAME" | passwd "$USERNAME" --stdin
    
USER "$USERNAME"

RUN set -ex \
    && mkdir -p $HOME/src $HOME/apps $HOME/log $HOME/tmp $HOME/oracle $HOME/rpc_file $HOME/uploadPath $HOME/backPath \
    && cat "$ZHTSYW_INIT"/conf/env_export >> $HOME/.bash_profile \
    && source $HOME/.bash_profile \
    && mkdir -p $HOME/envsoft \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/Python-3.4.2.tgz \
    && cd $HOME/envsoft/Python-3.4.2 \
    && ./configure --prefix=$HOME/apps/python34 --enable-shared \
    && make install \
    && ln -s $HOME/apps/python34/bin/python3 $HOME/apps/python34/bin/python34 \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/09pdf/setuptools-9.1.tar.gz \
    && cd $HOME/envsoft/setuptools-9.1 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/pip-10.0.1.tar.gz \
    && cd $HOME/envsoft/pip-10.0.1 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/psutil-2.2.0.tar.gz \
    && cd $HOME/envsoft/psutil-2.2.0 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/pymongo-2.7.2.tar.gz \
    && cd $HOME/envsoft/pymongo-2.7.2 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/PyYAML-3.10.tar.gz \
    && cd $HOME/envsoft/PyYAML-3.10 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/pycrypto-2.6.1.tar.gz \
    && cd $HOME/envsoft/pycrypto-2.6.1 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/ecdsa-0.13.tar.gz \
    && cd $HOME/envsoft/ecdsa-0.13 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/paramiko-1.15.2.tar.gz \
    && cd $HOME/envsoft/paramiko-1.15.2 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/MarkupSafe-0.23.tar.gz \
    && cd $HOME/envsoft/MarkupSafe-0.23 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/Mako-1.0.2.tar.gz \
    && cd $HOME/envsoft/Mako-1.0.2 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && unzip "$ZHTSYW_INIT"/software/03python/bitstring-3.1.5.zip \
    && cd $HOME/envsoft/bitstring-3.1.5 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/08Excel/jdcal-1.0.tar.gz \
    && cd $HOME/envsoft/jdcal-1.0 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/08Excel/openpyxl-2.2.3.tar.gz \
    && cd $HOME/envsoft/openpyxl-2.2.3 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && unzip "$ZHTSYW_INIT"/software/08Excel/xlwt3-0.1.2.zip \
    && cd $HOME/envsoft/xlwt3-0.1.2 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/08Excel/xlrd-0.9.3.tar.gz \
    && cd $HOME/envsoft/xlrd-0.9.3 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/09pdf/Pillow-2.9.0.tar.gz \
    && cd $HOME/envsoft/Pillow-2.9.0 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/09pdf/reportlab-3.2.0.tar.gz \
    && cd $HOME/envsoft/reportlab-3.2.0 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && unzip "$ZHTSYW_INIT"/software/10webservice/suds-jurko-0.6.zip \
    && cd $HOME/envsoft/suds-jurko-0.6 \
    && python3.4 setup.py install \
    && cd $HOME/envsoft \
    && tar zxf "$ZHTSYW_INIT"/software/03python/cx_Oracle-5.1.3.tar.gz \
    && cd $HOME/envsoft/cx_Oracle-5.1.3 \
    && python3.4 setup.py install \
    && cd $HOME/ \
    && rm -rf $HOME/envsoft

RUN set -ex \
    && mkdir -p $HOME/envsoft \
    && rm -rf $HOME/oracle/lib $HOME/oracle/bin \
    && mkdir -p $HOME/oracle/lib $HOME/oracle/bin \
    && cd $HOME/envsoft \
    && unzip "$ZHTSYW_INIT"/software/01oracle/instantclient-basic-linux.x64-11.2.0.4.0.zip \
    && unzip "$ZHTSYW_INIT"/software/01oracle/instantclient-sqlplus-linux.x64-11.2.0.4.0.zip \
    && mv $HOME/envsoft/instantclient_11_2/sqlplus $HOME/oracle/bin/sqlplus \
    && mv $HOME/envsoft/instantclient_11_2/* $HOME/oracle/lib \
    && ln -s $HOME/oracle/lib/libclntsh.so.11.1 $HOME/oracle/lib/libclntsh.so \
    && cd $HOME/envsoft \
    && unzip "$ZHTSYW_INIT"/software/01oracle/instantclient-sdk-linux.x64-11.2.0.4.0.zip \
    && rm -rf $HOME/oracle/sdk \
    && mv $HOME/envsoft/instantclient_11_2/sdk $HOME/oracle/sdk \
    && cd $HOME/ \
    && rm -rf $HOME/envsoft

CMD ["/bin/bash"]