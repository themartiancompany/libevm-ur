# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_offline="false"
_git="false"
_solc="true"
_hardhat="true"
_pkg=libevm
pkgname="${_pkg}"
pkgver="0.0.0.0.0.0.0.0.0.1.1.1.1.1.1"
_commit="23df8aaa8c852d541ca81b3c09e1b849953db3b4"
pkgrel=1
_pkgdesc=(
  "Bash library containing useful functions"
  "to write native applications interacting"
  "with EVM-compatible blockchain networks."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  'AGPL3'
)
depends=(
  "libcrash-bash"
)
optdepends=()
_os="$( \
  uname \
    -o)"
optdepends+=(
)
makedepends=(
  'make'
)
checkdepends=(
  "shellcheck"
)
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
if [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum='4c3cb149e3a03fd5866b0e38cf3a74cffccc7c88b50fee5a46b97607fd2ab776'
  fi
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)

validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
)

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  local \
    _make_opts=()
  _make_opts=(
    PREFIX="/usr"
    DESTDIR="${pkgdir}"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install
}

# vim: ft=sh syn=sh et
