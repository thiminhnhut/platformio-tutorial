##############################################
Project Configuration File ``platformion.ini``
##############################################

* **Thực hiện:** Thi Minh Nhựt - **Email:** `thiminhnhut\@gmail.com <thiminhnhut@gmail.com>`_

* **Thời gian:** Ngày 22 tháng 10 năm 2017

.. contents:: **Contents**

Nguồn tham khảo
****************

`Project Configuration File platformio.ini <http://docs.platformio.org/en/latest/projectconf.html>`_

PlatformIO Core settings: section ``[platformio]``
***************************************************

* Section ``[platformio]`` gồm các option sau: ``env_default``, ``home_dir``, ``lib_dir``, ``libdeps_dir``, ``lib_extra_dirs``, ``src_dir``, ``envs_dir``, ``data_dir``, ``test_dir`` và ``boards_dir``.

Option ``env_default``
=======================

* Bình thường khi build thì PlatformIO tự động build tất cả các environment trong section ``[env:NAME]``.

* Option ``env_default`` chỉ định chỉ build cho một số  environment.

* Ví dụ có 3 environment: ``[env:esp12e]``, ``[env:uno]`` và ``[env:d1]``. Muốn chỉ build cho ``[env:esp12e]`` thì khai báo ``env_default = esp12e``.

* Ví dụ:

  .. code-block:: ini

    ; platformion.ini

    [platformio]
    env_default = esp12e
    ; hoặc nhiều hơn thì ngăn cách bằng (comma + space)
    env_default = esp12e, uno

Option ``home_dir``
===================

* Option ``home_dir`` là nơi lưu trữ các platform toolchains, frameworks, global libraries for Library Dependency Finder, service data and etc.

* Giá trị mặc định của option ``home_dir`` trên Unix là ``home_dir = ~/.platformio``.

Option ``lib_dir``
===================

* Option ``lib_dir`` là nơi đặt các thư viện riêng (thư viện tự tạo). Giá trị mặc định của option ``lib_dir`` là ``lib_dir = lib``

* Quy định về cấu trúc file thư viện:

  + Mỗi thư viện nên được đặt trong một thư mục riêng, ví dụ: ``lib/private_lib/[here are source files]``

  + Các thư viện này sẽ có độ ưu tiên cao nhất.

* Include thư viện vào file ``src/main.cpp`` chỉ cần include ``lib.h`` (không cần include đường dẫn).

Option ``libdeps_dir``
=======================

* Option ``libdeps_dir`` là nơi lưu trữ các thư viện phụ thuộc được cài đặt cho project.

* Giá trị mặc định của option ``libdeps_dir`` là ``libdeps_dir = .piolibdeps``

* Các thư viện phụ thuộc này được cài đặt bởi option ``lib_deps`` trong section ``[env: NAME]``.

Option ``lib_extra_dirs``
=========================

* Option ``lib_extra_dirs`` gồm danh sách các đường dẫn chứa thư viện mà khi biên dịch chương trình sẽ tìm kiếm các thư viện trong danh sách các đường dẫn này.

* Option ``lib_extra_dirs`` này cũng có trong section ``[env: NAME]``. Sự khác nhau như sau:

  + Option ``lib_extra_dirs`` trong section ``[platformio]`` ảnh hưởng đến tất cả các section ``[env: NAME]``.

  + Option ``lib_extra_dirs`` trong section ``[env: NAME]`` chỉ ảnh hưởng đến ``[env: NAME]`` của nó.

* Ví dụ:

  .. code-block:: ini

    ; platformion.ini

    [platformio]
    lib_extra_dirs = /home/minhnhut/libaries, /home/minhnhut/Arduino/libraries

    ; hoặc khai báo theo từng dòng
    lib_extra_dirs =
      /home/minhnhut/libaries
      /home/minhnhut/Arduino/libraries

Option ``src_dir``
===================

* Option ``src_dir`` là đường dẫn đến source chính của project. Giá trị mặc định của option ``src_dir`` là ``src_dir = src``.

Option ``envs_dir``
===================

* Khi build thư mục này dùng để lưu trữ các compiled object files, static libraries, firmwares and other cached information. Cho phép PlatformIO build mã nguồn cực nhanh.

* Có thể xóa thư mục này và không làm ảnh hưỡng đến mã nguồn. Nếu chỉnh xử file ``platformio.ini`` thì thư mục này được xóa và sẽ được tự động tạo ra ở lần build tiếp theo.

* Giá trị mặc định của option ``envs_dir`` là ``envs_dir = .pioenvs``

Environment settings: section ``[env:NAME]``
*********************************************
